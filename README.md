# 🚦 Traffic Signal FSM — Verilog

A simple **Finite State Machine (FSM)** based traffic signal controller designed in **Verilog HDL**.

This project models a three-state traffic light sequence:

**RED → GREEN → YELLOW → RED**

The state transitions are controlled using a clock-driven counter.

---

## 🔄 How It Works

| State     | Code     |        Duration |
| --------- | -------- | --------------: |
| 🔴 RED    | `3'b100` | 10 clock cycles |
| 🟢 GREEN  | `3'b010` | 10 clock cycles |
| 🟡 YELLOW | `3'b001` |  3 clock cycles |

The counter resets whenever the FSM changes to a new state.

### FSM Flow

```text
        ┌──────────┐
        │   RED    │
        │  100     │
        └────┬─────┘
             │ 10 cycles
             ▼
        ┌──────────┐
        │  GREEN   │
        │  010     │
        └────┬─────┘
             │ 10 cycles
             ▼
        ┌──────────┐
        │  YELLOW  │
        │  001     │
        └────┬─────┘
             │ 3 cycles
             └──────────► RED
```

---

## 🧠 Design

The controller uses:

* **3-bit state register** for RED, GREEN and YELLOW
* **4-bit counter** for state timing
* **Synchronous active-high reset**
* **Positive-edge triggered clock**
* `case` statement for FSM state transitions

The main idea is:

```text
Clock → State Register → Current State
                    ↓
                 Counter
                    ↓
             Next State Logic
                    ↓
               State Update
```

---

## 🧪 Verification

The design was simulated using a Verilog testbench.

Simulation checks:

* Reset operation
* RED → GREEN transition
* GREEN → YELLOW transition
* YELLOW → RED transition
* Counter reset during state changes

The simulation waveform was generated as a **VCD file** and inspected using GTKWave.

---

## ⚙️ Synthesis

The RTL was synthesized using **Yosys**.

The synthesized design was exported as:

`traffic_netlist.v`

The netlist contains the synthesized combinational logic and sequential elements corresponding to the FSM and counter.

---

## 🛠️ Tools Used

* **Verilog HDL**
* **Icarus Verilog** — Simulation
* **GTKWave** — Waveform analysis
* **Yosys** — RTL synthesis
* **Ubuntu / WSL** — Development environment

---

## 📁 Project Files

```text
traffic.v              → RTL design
traffic_tb.v           → Testbench
traffic.vcd             → Simulation waveform
traffic_netlist.v       → Synthesized netlist
traffic_output.pdf      → Waveform output
```

---

## 🎯 What I Learned

This project helped me understand the complete basic RTL flow:

**FSM Design → Verilog RTL → Testbench → Simulation → Waveform Analysis → Synthesis → Netlist**

It also gave me practical experience with synchronous logic, counters, state transitions, and RTL synthesis.

---

### 👩‍💻 Author

**Preethi K N**

Electronics & Communication Engineering
Focused on **Digital Design & VLSI**
