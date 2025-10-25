# 4Bit-Up-Down-Asynchronous-Reset-Counter-Synthesis

## Aim:

Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

◦ SDC (Synopsis Design Constraint) File (.sdc)

 ### Step 2 : Creating an SDC File

•	In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

•	The SDC File must contain the following commands;

create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

set_clock_transition -rise 0.1 [get_clocks "clk"]

set_clock_transition -fall 0.1 [get_clocks "clk"]

set_clock_uncertainty 0.01 [get_ports "clk"]

set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

ii, iii → Sets Clock Rise and Fall time to 100ps.

iv → Sets Clock Uncertainty to 10ps.

v, vi → Sets the maximum limit for I/O port delay to 1ps.

### Step 3 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :
<img width="1665" height="1108" alt="Screenshot 2025-10-24 215124" src="https://github.com/user-attachments/assets/7bc22dfb-c4a7-4358-8c5f-d14ccd65361b" />

#### Area report:
<img width="1915" height="845" alt="Screenshot 2025-10-24 215149" src="https://github.com/user-attachments/assets/bdbb1ddc-0b29-46cc-b234-993585f66f0e" />

#### Power Report:
<img width="1913" height="1050" alt="Screenshot 2025-10-24 215201" src="https://github.com/user-attachments/assets/a15cf7e1-0629-414e-8553-3e3c70a7a85d" />

#### Timing Report: 
<img width="1915" height="1047" alt="Screenshot 2025-10-24 215213" src="https://github.com/user-attachments/assets/f3fd419d-0ad6-452e-b82d-d82f0ad243bb" />

#### Result: 

The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.





