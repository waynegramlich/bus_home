# Bus Home

## Introduction

This is a the top level documentation for "Bus".
"Bus" is a place holder name until someone comes along with
a less generic name.  Possibilities are "MakerBus", "HackerBus",
"UbiquiBus", "RoBus", "FunBus", "BlastBus", etc.  Ultimately
somebody in "marketing" picks the name.  For now, it is just
called "Bus".

Bus is an inexpensive interprocessor communication bus that
uses UART's running at .5MHz running on top of the ISO-11898
electrical standard (i.e. CAN bus physical layer.)  While Bus 
was initially designed for robot applications, it has many uses
outside of robotics.  With Bus, it is possible to have multiple
coordinated sensors, actuators, computation nodes to solve
complex real-time applications.

## Modules Directory

The modules directory is partitioned into 4 catagories:

* Works.

* In Development.

* Not Started.

* Deprecated.

### Working Modules

The following working modules exist:

* [bus_beaglebone](https://github.com/waynegramlich/bus_beaglebone)
  This module connects a BeagleBone Black to Bus.
  (Status: Works)

* [bus_bridge_encoders_sonar](https://github.com/waynegramlich/bus_bridge_encoders_sonar):
  This module provides 1) two 1 Ampere H-Bridges to drive two
  small motors, 2) two wheel encoder inputs, and 3) two HC-SR04 sonars.

* [bus_power](https://github.com/waynegramlich/bus_power):
  This module is a power distribution board for Bus.  It has an
  On/Off switch and requires two batteries.  There are 6 Ampere
  fuses for each bus.
  
* [bus_raspberry_pi](https://github.com/waynegramlich/bus_raspberry_pi):
  This module connects a Rasbperry Pi Model B+ to Bus.

* [bus_splice](https://github.com/waynegramlich/bus_splice):
  This module provides the ability to splice two 10-wire bus
  cables together.

* [bus_sonar10](https://github.com/waynegramlich/bus_sonar10):
  This module drives up to 10 of the popular HC-SR04 sonar modules.

* [bus_usb_power](https://github.com/waynegramlich/bus_usb_power):
  This module is a power distribution board for Bus.  It can take
  power in via either a batteryp or via a USB power pack.  Depending
  upon which DC/DC regulatars are plugged in, it can generate up 2A@5V
  on a pair of USB power recepticles.  Likewise, it provides power
  to to the `LPWR` and `BPWR` lines on the bus.

### Modules Being Developed:

The following modules are being developed:

* [bus_battery](https://github.com/waynegramlich/bus_battery):
  (Status: waiting firmware)

* bus_dynabus:
  This module will talk to one of the two Robotis<Sup>&reg;</Sup>
  Dynamixel<Sup>&reg;</Sup> servo buses like the popular AX12's.
  (Status: Schematic being worked on.)

* [bus_grove12](https://github.com/waynegramlich/bus_grove12):
  This module provides 12 connectors that connect to the
  [grove system](http://www.seeedstudio.com/wiki/GROVE_System)
  modules developed by
  [SeeedStudio](http://www.seeedstudio.com/).
  The grove system is a family of over a 100 modules with a standard
  cable connector and some fairly standard mounting holes.
  (Status: waiting for firmware)

* [bus_servo8](https://github.com/waynegramlich/bus_servo8):
  This module will drive up 8 hobby servos.  It has an on-board
  regulator for 5 volts to power servos at 1.5 Amperes.
  (Status: waiting for firmware)

* [bus_servo32](https://github.com/waynegramlich/bus_servo32):
  This module will drive up to 32 hobby servos.  It has an on-board
  regulator for 5 volts to power servos at 3 Amperes.
  (Status: schematic mostly done; pcb layout started)

* [bus_shield](https://github.com/waynegramlich/bus_shield):
  This module is allows you to plug in an Arduino<Sup>&reg;</Sup>
  compatible shield and talk to it.  The serial pins (D0, D1)
  are not available to the shield since they are used to talk
  to the bus.
  (Status: Rev. A is ready for manufacture.)

* [bus_splice](https://github.com/waynegramlich/bus_splice):
  This module is used to splice to bus cables together.
  (Status: Waiting for assembly; should "just work")

### Modules Not Yet Started

* bus_imu:
  This module provides a 3-axis compass, 3-axis gyro, 3-axis
  accelerometer and a barameter altimeter.

* bus_lcd32:
  This module will provide a 32 character LCD display organized
  as two lines of 16.

* bus_microbusN:
  This module provides connections for up to N mikroBUS<Sup>&reg;</Sup>
  compatible modules.  mikroBUS is a bus standard developed by
  [MikroElectronika](http://www.mikroe.com/).  MikroElectronika has
  over hundred Click<Sup>&reg;</Sup> boards that plug into the
  mikroBUS connector footprint.  Both mikroBus<Sup>&reg;</Sup>
  and Click<Sup>&reg;</Sup> are trademarked by MicroElectronika.
  Thus, the board is called "microbusN" to avoid trade-mark infringement.

* bus_speech:
  This module provides a text to speech capability using the following
    [speech chip](http://www.speechchips.com/shop/item.aspx?itemid=22)
  as its basis.

### Deprecated Modules

The following modules are deprecated:

* [busino](https://github.com/waynegramlich/busino):
  This module is a hybrid design that supports both
   Arduino<Sup>&reg;</Sup> compatible shields and a up to 4
   "mini-shields".  The list of  developed mini-shields are
  listed below:

  * [mini_bridge_encoders_sonar](https://github.com/waynegramlich/mini_bridge_encoders_sonar):
    This mini shield can drive two motors, 2 quadrature encoders
    and two sonars.
    (Status: Works)

  * [mini_beaglebone_black](https://github.com/waynegramlich/mini_beaglebone_black)
    This mini shield connects to the BeagleBone Black.
    (Status: Works)

  * [mini_raspberry_pi](https://github.com/waynegramlich/mini_raspberry_pi)
    This mini shield connects to the Raspberry Pi
    (Status: Works)

  * [mini_power](https://github.com/waynegramlich/mini_power)
    This mini shield provides battery power.
    (Status: Works)

  This module has a lot of connectors and the mini-shields are really
  too small.
  (Status: deprecated)

## Electrical Specifications

The minimal electrical requirement for Bus module is
.5MHz slope controlled ISO-11898.  ISO-11898 is the
CAN bus physical layer.  ISO-11809 is implemented using
3 wires.

The preferred Bus electrical cable is a 10 wire ribbon
cable where the additional wires are used to supply
power and ground return.

### Minimal Electrical Specification

The absolute minimum electrical requirement for a Bus node
to implement is ISO-11898.  ISO-11898 was primarily designed
to provide a very reliable communication layer for the
automotive industry.  In the automotive industry, the CAN
(Controller Area Network) bus protocol is quite prevalent
and it exclusively uses ISO-11898. Indeed, the ISO-11898
transceivers are usually marketed as "CAN Transceivers".

ISO-11898 requires 3-wires:

* Ground
* CANH
* CANL

The CANH and CANL wires form a differential pair that can be
used to reliably send a 1 or a 0.  A differential pair has
higher noise immunity than a single wire.  The ISO-11898 also
requires a common ground wire.

While ISO-11898 can be used to communicate at speeds up to
1MHz, the generated square waves produce a fair amount of
radiated electromagnetic interference (EMI.)  Alternatively,
ISO-11898 can be run at slower speeds in a mode called slope
control that results in trapazoidal waves which radiate much
less EMI.  Most  automotive applications run at a slope controlled
speed of either .25MHz or .5MHz.  Bus runs at .5Mhz with in
slope control mode.  When running at .5Mhz, the bus can be
up to 100 meters long.

Both ends of the bus must have a 120 Ohm resister
attached across the CANH and CANL wires to eliminate
signal reflections.

ISO-11898 provides a half duplex bus.  With a half
duplex bus whatever is transmitted on the bus is
received by all nodes on the bus.  This includes
the node that is doing the transmitting.

In addition, ISO-11898 allows more than one node to
transmit at the same time.  The table below shows
the behavior:

<BlockQuote>
    <Table Border="1">
      <TR>
	<TH ColSpan="5">Transmits</TH>
	<TH RowSpan="2">All<Br>Receive</TH>
      </TR><TR>
	<TH>Node 1</TH>
	<TH>Node 2</TH>
	<TH>Node 3</TH>
	<TH>...</TH>
	<TH>Node N</TH>
      </TR><TR>
	<TD>1</TD>
	<TD>1</TD>
	<TD>1</TD>
	<TD>...</TD>
	<TD>1</TD>
	<TD>1</TD>
      </TR><TR>
	<TD>0</TD>
	<TD>x</TD>
	<TD>x</TD>
	<TD>...</TD>
	<TD>x</TD>
	<TD>0</TD>
      </TR><TR>
	<TD>x</TD>
	<TD>0</TD>
	<TD>x</TD>
	<TD>...</TD>
	<TD>x</TD>
	<TD>0</TD>
      </TR><TR>
	<TD>x</TD>
	<TD>x</TD>
	<TD>0</TD>
	<TD>...</TD>
	<TD>x</TD>
	<TD>0</TD>
      </TR><TR>
	<TD ColSpan="6">...</TD>
      </TR><TR>
	<TD>x</TD>
	<TD>x</TD>
	<TD>x</TD>
	<TD>...</TD>
	<TD>0</TD>
	<TD>0</TD>
      </TR>
    </Table>
</BlockQuote>
A 1 is received only if all bus nodes are transmitting
a 1.  If any node transmits a 0, all nodes receive a 0.

In short summary, the minimum Bus requirement is ISO-11898
running at .5MHz in slope controlled mode.  Both ends of
the bus must be terminated with a 120 Ohm resistor.

<BlockQuote>
    *{ Talk about polarity protection here. }*
</BlockQuote>

<BlockQuote>
    *{ Talk about current limiting here. }*
</BlockQuote>

### 10-Wire Bus Electrical Specification

For now, only a 10-wire implementation of Bus is defined.
Presumably, over time additional interoperable versions
will probably be defined.

The 10-wire Bus has 10 wires organized as three pair groupings:

* CANH(1)/CANL(1)

* LPWR(2)/LGND(2)

* MPWR(2)/MGND(2)

CANH/CANL are the differential communication pair
required by ISO-11898.  LPWR/LGND are a logic power
and ground pair that is used to provide electrical
power for Bus Nodes.  MPWR/MGND is an electrically
isolated power bus that is primarily used to power
small motors and servos.  The LPWR, LGND, MPWR, and
MGND wires have two wires to double current capacity.

The 10-wire Bus connector is a polarized shrouded 2 by 5
male pin header with a pin pitch of 2.54mm (i.e. .1 inch).
This connector is compatible with a female ribbon cable
insulation displacement connector (IDC.)  This connector
was selected because it is inexpensive, readily available
from multiple vendors, and easy to attach to 10 conductor
1.27mm (.05 inch pitch) ribbon cable.  The ribbon cable is
also relatively inexpensive and is available from multiple
vendors.

Since there are other systems that use the 2 by 5 polarized
shrouded header, the Bus connectors should be gray or white.
This is a feeble attempt to discourage people from plugging
incompatible buses together.

The connector is connected as follows:
<BlockQuote>
    <Table Border="1">
      <TR>
	<TH>Name</TH>
	<TH>Pin</TH>
	<TH>Pin</TH>
	<TH>Name</TH>
	<TH>Notes</TH>
      </TR><TR>
	<TD>LPWR1</TD>
	<TD>1</TD>
	<TD>2</TD>
	<TD>LPWR2</TD>
	<TD>LPWR1/LPWR2 electrically connected</TD>
      </TR><TR>
	<TD>LGND1</TD>
	<TD>3</TD>
	<TD>4</TD>
	<TD>LGND2</TD>
	<TD>LGND1/LGND2 electrically connected</TD>
      </TR><TR>
	<TD>CANH</TD>
	<TD>5</TD>
	<TD>6</TD>
	<TD>CANL</TD>
      </TR><TR>
	<TD>MGND1</TD>
	<TD>7</TD>
	<TD>8</TD>
	<TD>MGND2</TD>
	<TD>MGND1/MGND2 electrically connected</TD>
      </TR><TR>
	<TD>MPWR1</TD>
	<TD>9</TD>
	<TD>10</TD>
	<TD>MPWR2</TD>
	<TD>MPWR1/MPWR2 electrically connected</TD>
      </TR>
    </Table>
</BlockQuote>
By assigning 2 ribbon cable conductors to each of LPWR, LGND,
MPWR, and MGND, the allowable current is doubled.

All Bus modules are required to accept up to 30V on either
LPWR and/or MPWR.  30V was selected to be compatible with 24V
battery systems.  A fully charged 24V battery can sometimes
get to a voltage as high 28V.

If the female IDC connector is accidentally attached to the
cable with the pins reversed, a Bus module that is plugged
into the  reversed connector will get its logic power from
MPWR and MGND.  Since both power buses are specified to take
up to 30V, the Bus module will not suffer any electrical damage.
In this situatation, the CANH/CANL pairs will also be reversed
which will preclude successful operation.  Again, no electrical
damage will occur.

<BlockQuote>
  *{ More goes here. }*
</BlockQuote>
