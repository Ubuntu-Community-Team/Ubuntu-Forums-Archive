---
title: "Canon scanner recognized but won't calibrate"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by llogan on 2009-02-06
Hi,

I am trying to get my Canon FB630P flatbed scanner to work.  I have installed the canon_pp driver from the SANE Project site and read all the README's.  I have checked that 'canon_pp' is uncommented in '/etc/sane.d/dll.conf' and the correct port is selected in 'canon_pp'.  My BIOS is set for EEP+ECP.  I am runnning everything as root so that permissions aren't a problem.  Here is the result of my work so far... 

llogan@alpha:~$ sudo SANE_DEBUG_CANON_PP=255 scanimage -L
[sanei_debug] Setting debug level of canon_pp to 255.
[canon_pp] >> sane_init(0xbfda44b8, 0x804d520): sane-backends 1.0.19
[canon_pp] sane_init: >> ieee1284_find_ports
[canon_pp] sane_init: 0 << ieee1284_find_ports
[canon_pp] sane_init: 1 parallel port(s) found.
[canon_pp] sane_init: port parport0
[canon_pp] >> init_device
[canon_pp] init_device: [configuring options]
[canon_pp] init_device: configuring opt: num_options
[canon_pp] init_device: configuring opt: resolution
[canon_pp] init_device: configuring opt: colour mode
[canon_pp] init_device: configuring opt: bit depth
[canon_pp] init_device: configuring opt: tl-x
[canon_pp] init_device: configuring opt: tl-y
[canon_pp] init_device: configuring opt: br-x
[canon_pp] init_device: configuring opt: br-y
[canon_pp] init_device: configuring opt: calibrate
[canon_pp] init_device: done opts
[canon_pp] << init_device
[canon_pp] sane_init: ># Define which port to use if one isn't specified - you should only have<
[canon_pp] sane_init: ># one of these lines!<
[canon_pp] sane_init: ># This is the default port to be used - others will be detected<
[canon_pp] sane_init: >ieee1284 parport0<
[canon_pp] sane_init: Successfully parsed default scanner.
[canon_pp] sane_init: ><
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># Define the location of our pixel weight file, can begin with ~/ if needed.<
[canon_pp] sane_init: ># You can have as many of these as you like - lines with ports that don't exist<
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># will be ignored.<
[canon_pp] sane_init: >#<
[canon_pp] sane_init: ># Parameters are:<
[canon_pp] sane_init: ># calibrate /path/to/calibration-file port-name<
[canon_pp] sane_init: >#<
[canon_pp] sane_init: ># The format of port-name is dependant on your OS version.<
[canon_pp] sane_init: >#<
[canon_pp] sane_init: ># If a file isn't speficied, the default name will be<
[canon_pp] sane_init: ># ~/.sane/canon_pp-calibration-[port-name]<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >#This first one was the original - LP<
[canon_pp] sane_init: >calibrate ~/.sane/canon_pp-calibration-pp0 parport0<
[canon_pp] sane_init: calibrate line, calibrate ~/.sane/canon_pp-calibration-pp0 parport0
[canon_pp] sane_init: Finding scanner on port 'parport0'
[canon_pp] sane_init: Found!
[canon_pp] sane_init: Parsed cal, for port 'parport0', weight file is '~/.sane/canon_pp-calibration-pp0'.
[canon_pp] sane_init: >#calibrate ~/.sane/canon_pp-calibration parport0<
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># calibrate /etc/sane/my_calibration parport1<
[canon_pp] sane_init: ><
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># Enable the next line if you're having trouble with ECP mode such as I/O<
[canon_pp] sane_init: ># errors.  Nibble mode is slower, but more reliable.<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >#force_nibble<
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># Set a default initialisation mode for each port.  Valid modes are:<
[canon_pp] sane_init: ># AUTO		(attempts to automatically detect by trying both methods)<
[canon_pp] sane_init: ># FB620P	(10101010 style.. also works for FB320P)<
[canon_pp] sane_init: >#FB630P	(11001100 style.. also works for FB330P, N340P, N640P)<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >#init_mode AUTO parport0<
[canon_pp] sane_init: ># init_mode FB620P parport0<
[canon_pp] sane_init: >init_mode FB630P parport0<
[canon_pp] sane_init: Parsed init.
[canon_pp] detect_mode: Opening port parport0
[canon_pp] detect_mode: Claiming port.
[canon_pp] detect_mode: Port supports ECP-H.
[canon_pp] detect_mode: Port supports interrupts.
[canon_pp] detect_mode: Port supports DMA.
[canon_pp] detect_mode: Using ECP-H Mode
[canon_pp] sane_init: >> initialise
[canon_pp] Scanner not ready (0xb). Attempting to reset...
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Had to reset scanner, waiting for the head to get back.
[canon_pp] initialise: >> scanner_init
[canon_pp] NEW Send Command (length 10):
[canon_pp] << write[canon_pp] * Check Status:
[canon_pp] NEW read_data (2 bytes):
[canon_pp] -> ieee_transfer(2) *
[canon_pp] IEEE transfer (2 bytes)
[canon_pp] <- (2)
[canon_pp] !! Invalid Command - 0x1515
[canon_pp] NEW Send Command (length 10):
[canon_pp] << write[canon_pp] * Check Status:
[canon_pp] NEW read_data (2 bytes):
[canon_pp] -> ieee_transfer(2) *
[canon_pp] IEEE transfer (2 bytes)
[canon_pp] <- (2)
[canon_pp] Ready - 0x0606
[canon_pp] initialise: << scanner_init
[canon_pp] NEW Send Command (length 10):
[canon_pp] << write[canon_pp] * Check Status:
[canon_pp] NEW read_data (2 bytes):
[canon_pp] -> ieee_transfer(2) *
[canon_pp] IEEE transfer (2 bytes)
[canon_pp] <- (2)
[canon_pp] Ready - 0x0606
[canon_pp] NEW read_data (38 bytes):
[canon_pp] -> ieee_transfer(38) *
[canon_pp] IEEE transfer (38 bytes)
[canon_pp] <- (38)
[canon_pp] NEW Send Command (length 10):
[canon_pp] << write[canon_pp] * Check Status:
[canon_pp] NEW read_data (2 bytes):
[canon_pp] -> ieee_transfer(2) *
[canon_pp] IEEE transfer (2 bytes)
[canon_pp] <- (2)
[canon_pp] Ready - 0x0606
[canon_pp] NEW read_data (12 bytes):
[canon_pp] -> ieee_transfer(12) *
[canon_pp] IEEE transfer (12 bytes)
[canon_pp] <- (12)
[canon_pp] sane_init: << 0 initialise
[canon_pp] sane_init: And back to sleep again
[canon_pp] NEW Send Command (length 10):
[canon_pp] << write[canon_pp] * Check Status:
[canon_pp] NEW read_data (2 bytes):
[canon_pp] -> ieee_transfer(2) *
[canon_pp] IEEE transfer (2 bytes)
[canon_pp] <- (2)
[canon_pp] Ready - 0x0606
[canon_pp] fix_weights_file: Calibration file is good for opening!         #Looks like good news...
[canon_pp] << sane_init
[canon_pp] >> sane_get_devices (0xbfda4518, 0)
[canon_pp] << sane_get_devices
device `canon_pp:parport0' is a CANON FB630P flatbed scanner
[canon_pp] >> sane_exit
[canon_pp] << sane_exit

llogan@alpha:~$ sudo scan -C
Canon CanoScan(tm) Scanner Driver 6.00. Copyright (C) 2001 Simon Krix et al.
This driver comes with ABSOLUTELY NO WARRANTY; for details
please see [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html)
This is free software, and you are welcome to redistribute
it under certain conditions.
See the GNU General Public License for details.

Finding IEEE1284 ports...
    parport0 (0x378): <raw><cpt><nbl><byt><ecp><swe><irq><dma>... OK (ecp).

Detecting scanner:
 ID:	"CANON   IX-06075E       1.00"
 Model:	FB630P   (600x600dpi,  5104x7016 pixels)
Calibrating 5104x6 pixels calibration image (38280 bytes each scan).
Step 1/3: Calibrating black level...
  * Black scan number 1/3.

			...and it just hangs here for hours until I CTL+Z.  It's strange, because it says above "[canon_pp] fix_weights_file: Calibration file is good for opening!". I have tried this with 'force nibble' both commented and uncommented.  I have read the README's and googled countless similiar postings both in this forum and just about everywhere else.  If anybody has any advice, suggestions or comments I would be very glad to hear them.

---

### Post by llogan on 2009-02-11
Hi,

I decided to give up on the CanoScan FB60P and pick up an inexpensive HP ScanJet G3010 ($50 Cdn new).  Worked just fine after downloading and configuring the proper driver from the SANE Project. The ScanJet just wasn't worth the hassle...

---

### Post by klytu on 2009-02-15
> **llogan said:**
> Hi,

I decided to give up on the CanoScan FB60P and pick up an inexpensive HP ScanJet G3010 ($50 Cdn new).  Worked just fine after downloading and configuring the proper driver from the SANE Project. The ScanJet just wasn't worth the hassle...

Yeah, I seem to be one of the few people left who hasn't given up on the FB620P. On my system it works great for grayscale scanning & preview, but preview chokes most of the time for color. I first noticed the issue when I upgraded from Feisty to Hardy Heron. It's weird but I can often scan in color by previewing in gray scale, selecting the scan area, and then scanning in color.  I am reasonably sure the problem is software related. For example, I can pop in a Knoppix CD that uses xsane version 0.991 (Hardy uses version 0.995) and I can still preview & scan perfectly well in both grayscale and color.

Anyway, good luck with your new scanner.

---

