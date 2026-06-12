---
title: "Hangs on loading screen"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by zippymel on 2009-04-26
Installed via Wubi for dualboot under XP... Yesterday it was working but today :(, here what happened and what I did earlier:

Got the ubuntu screen with the orange progression bar. After completed, here's what it exactly shows :

Warning : Fake start-stop-daemon called, doing nothing. 
   ... done.
   *Starting bluetooth (but I have nothing bluetooth lol)

Warning : Fake start-stop-daemon called, doing nothing. 
   ... done.
/etc/rc2.d/S98usplash: 112: clear: not found
/etc/rc2.d/S99acpi-supprot: line 7: /srt/share/acip-support/power-funcs : no such file or directory
*Checking battery state...
etc/acpi/start.d/10-save-dmidecode.sh : line 9: dmidecode : command not found
etc/acpi/start.d/10-save-dmidecode.sh : line 10: dmidecode : command not found
etc/acpi/start.d/10-save-dmidecode.sh : line 11: dmidecode : command not found
etc/acpi/start.d/10-save-dmidecode.sh : line 12: dmidecode : command not found
etc/acpi/start.d/60-asus-wireless-led.sh: line 2: /usr/share/acpi-support/state-funcs: No such file or directory
etc/acpi/start.d/60-asus-wireless-led.sh: line 3: isAnyWirellessPoweredOn: command not found
acpi/start.d/60-asus-wireless-led.sh: line 6: setLEDAsusWireless: command not found
etc/acpi/start.d/90-pdparam.sh: line 10: /usr/share/acpi-support/power-funcs: no such file or directory
etc/acpi/start.d/90-pdparam.sh: line 23: getState: command not found
   ...done.

Then nothing else...:confused:

If I press Ctrl-Alt-Del :
[init: tty4 main process (2530) killed by TERM signal
init: tty5 main process (2531) killed by TERM signal
init: tty2 main process (2537) killed by TERM signal
init: tty3 main process (2538 ) killed by TERM signal
init: tty6 main process (2539) killed by TERM signal
init: tty1 main process (2726) killed by TERM signal
usplach: No usable theme found for 1024x768
screen init failed
   *Saving the system clock

Need to reboot the PC

Dual boot choice : XP or Ubuntu... Ubunto chosen then ESC for more option
Tried some $ cp command found and tried to add sudo user... nothing...

Please help... I'm desesperate... :cry:

Do I try to uninstall-Ubuntu.exe coming from Wubi and try again or there is other option?

Thank you

---

