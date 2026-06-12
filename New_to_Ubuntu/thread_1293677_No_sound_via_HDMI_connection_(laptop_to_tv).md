---
title: "No sound via HDMI connection (laptop to tv)"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by barcelonic on 2009-10-17
OK so this is my very first day with Ubuntu and im very impressed so far. However, i used to use Vista and had an HDMI cable connecting my laptop to my plasma TV.

I managed to get the picture set up fine with Ubuntu but there is no sound. This is a system issue so does anyone know how to resolve it?

As I said this is not a hardware issue and has nothing to do with the connection because earlier today I was using this cable with a Vista PC to the same television.

Any ideas please? :)

---

### Post by coldReactive on 2009-10-17
Output **gksudo lspci -vv** (from terminal) to us wrapped in code bbcode.

---

### Post by barcelonic on 2009-10-17
> **coldReactive said:**
> Output **gksudo lspci -vv** (from terminal) to us wrapped in code bbcode.

gksudo: invalid option -- 'v'
GKsu version 2.0.2

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.

---

### Post by coldReactive on 2009-10-17
Dammit, gksu *slaps it upside the head.*

output **lspci**

---

### Post by barcelonic on 2009-10-17
> **coldReactive said:**
> Dammit, gksu *slaps it upside the head.*

output **lspci**

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
06:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)

---

### Post by barcelonic on 2009-10-17
OK problem solved.Took ages but i finally found the correct solution online (after muddling my way through a lot more complicated solutions first, none of which worked).

For anyone else having the same problem, try this before checking your drivers etc..  :

[I]In System > Sound > Prefs make sure the HDMI option is selected for in all applicable boxes.

Then right click the speaker on your top panel and Open Volume Control. MAke sure the same HDMI device is selected in the top menu. Click Preferences and check the box next to IEC958.

Then on the Switches tab in vol control check the box IEC958 and you should be good to go!! [/I]

---

