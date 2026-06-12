---
title: "[SOLVED] WiCD blinking on network traffic workaround"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by carlotheman on 2008-04-13
Here's a workaround to WiCD 1.4 constantly blinking when there is network traffic... I find that quit irritating. Take this script and run it as root: It replaces all the blinky images in wicd with hard links to the original, hence removing the blinkiness. Hopefully there will be a preferences option soon.

#!/bin/sh

rm /opt/wicd/images/transmitting*
rm /opt/wicd/images/receiving*
rm /opt/wicd/images/both*
rm /opt/wicd/images/idle*

ln /opt/wicd/images/bad-signal-lock.png /opt/wicd/images/transmitting-bad-signal-lock.png
ln /opt/wicd/images/bad-signal.png /opt/wicd/images/transmitting-bad-signal.png
ln /opt/wicd/images/good-signal-lock.png /opt/wicd/images/transmitting-good-signal-lock.png
ln /opt/wicd/images/good-signal.png /opt/wicd/images/transmitting-good-signal.png.png
ln /opt/wicd/images/high-signal-lock.png /opt/wicd/images/transmitting-high-signal-lock.png
ln /opt/wicd/images/high-signal.png /opt/wicd/images/transmitting-high-signal.png.png
ln /opt/wicd/images/low-signal-lock.png /opt/wicd/images/transmitting-low-signal-lock.png
ln /opt/wicd/images/low-signal.png /opt/wicd/images/transmitting-low-signal.png

ln /opt/wicd/images/bad-signal-lock.png /opt/wicd/images/receiving-bad-signal-lock.png
ln /opt/wicd/images/bad-signal.png /opt/wicd/images/receiving-bad-signal.png
ln /opt/wicd/images/good-signal-lock.png /opt/wicd/images/receiving-good-signal-lock.png
ln /opt/wicd/images/good-signal.png /opt/wicd/images/receiving-good-signal.png.png
ln /opt/wicd/images/high-signal-lock.png /opt/wicd/images/receiving-high-signal-lock.png
ln /opt/wicd/images/high-signal.png /opt/wicd/images/receiving-high-signal.png.png
ln /opt/wicd/images/low-signal-lock.png /opt/wicd/images/receiving-low-signal-lock.png
ln /opt/wicd/images/low-signal.png /opt/wicd/images/receiving-low-signal.png

ln /opt/wicd/images/bad-signal-lock.png /opt/wicd/images/both-bad-signal-lock.png
ln /opt/wicd/images/bad-signal.png /opt/wicd/images/both-bad-signal.png
ln /opt/wicd/images/good-signal-lock.png /opt/wicd/images/both-good-signal-lock.png
ln /opt/wicd/images/good-signal.png /opt/wicd/images/both-good-signal.png.png
ln /opt/wicd/images/high-signal-lock.png /opt/wicd/images/both-high-signal-lock.png
ln /opt/wicd/images/high-signal.png /opt/wicd/images/both-high-signal.png.png
ln /opt/wicd/images/low-signal-lock.png /opt/wicd/images/both-low-signal-lock.png
ln /opt/wicd/images/low-signal.png /opt/wicd/images/both-low-signal.png

ln /opt/wicd/images/bad-signal-lock.png /opt/wicd/images/idle-bad-signal-lock.png
ln /opt/wicd/images/bad-signal.png /opt/wicd/images/idle-bad-signal.png
ln /opt/wicd/images/good-signal-lock.png /opt/wicd/images/idle-good-signal-lock.png
ln /opt/wicd/images/good-signal.png /opt/wicd/images/idle-good-signal.png.png
ln /opt/wicd/images/high-signal-lock.png /opt/wicd/images/idle-high-signal-lock.png
ln /opt/wicd/images/high-signal.png /opt/wicd/images/idle-high-signal.png.png
ln /opt/wicd/images/low-signal-lock.png /opt/wicd/images/idle-low-signal-lock.png
ln /opt/wicd/images/low-signal.png /opt/wicd/images/idle-low-signal.png

---

### Post by imdano on 2008-04-13
In 1.5.0 (the next version) you'll be able to turn it off with a command line argument.

---

