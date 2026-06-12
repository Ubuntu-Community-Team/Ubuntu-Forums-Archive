---
title: "Intel Centrino Advanced-N 6205 [Taylor Peak] / iwlwifi Intermittent Wifi Connection"
date: 2020-07-08
forum: Networking &amp; Wireless
---

### Post by hbn97kw4dp on 2020-07-08
I have a Dell Latitude E6230 running Ubuntu 20.04 (with [Regolith]("https://regolith-linux.org") desktop environment) which is having intermittent wifi connectivity problems.  On startup the wifi will either connect, connect after 20 minutes or not connect at all.  Typically once connected the connection will remain.  There doesn't seem to be any particular link between what I'm doing with the laptop and whether it will connect or not - apart from it seems to know when I really want to, and therefore won't...

In accordance with the [Before posting in Networking & Wireless]("https://ubuntuforums.org/showthread.php?t=370108") post I've pastebin'd my [wireless-info]("https://pastebin.com/vbcVa3RF").

Looking through the wireless-info there is one particularly noticeable element within dmesg:

```
[COLOR=#7A0874]**[**[/COLOR][COLOR=#000000]585.566540[/COLOR][COLOR=#7A0874]**]**[/COLOR][COLOR=#333333] iwlwifi 0000:02:[/COLOR][COLOR=#000000]00.0[/COLOR][COLOR=#333333]: Microcode SW error detected.  Restarting 0x2000000.[/COLOR]
```[COLOR=#333333]
I found some [advice on this problem]("https://forums.linuxmint.com/viewtopic.php?t=295219") on the Linux Mint forum and therefore tried to update my microcode, downloading the la[/COLOR][SIZE=2][FONT=arial][COLOR=#333333]test version from [Oregon State University FTP]("http://ftp.us.debian.org/debian/pool/non-free/a/amd64-microcode/").
[/COLOR][/FONT][/SIZE][SIZE=2][FONT=arial]
However on running the command:

[/FONT][/SIZE]```
[SIZE=2][FONT=arial]sudo dpkg -i intel-microcode_3.20200616.1_i386.deb[/FONT][/SIZE]
```

I got the following error:

```

(Reading database ... 185549 files and directories currently installed.)
[SIZE=2][FONT=arial]Preparing to unpack intel-microcode_3.20200616.1_i386.deb ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]Unpacking intel-microcode:i386 (3.20200616.1) over (3.20200609.0ubuntu0.20.04.2) ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]dpkg: dependency problems prevent configuration of intel-microcode:i386:[/FONT][/SIZE]
[SIZE=2][FONT=arial] intel-microcode:i386 depends on iucode-tool (>= 1.0).[/FONT][/SIZE]
[SIZE=2][FONT=arial]dpkg: error processing package intel-microcode:i386 (--install):[/FONT][/SIZE]
[SIZE=2][FONT=arial] dependency problems - leaving unconfigured[/FONT][/SIZE]
[SIZE=2][FONT=arial]Errors were encountered while processing:[/FONT][/SIZE]
[SIZE=2][FONT=arial] intel-microcode:i386[/FONT][/SIZE]

```
[SIZE=2][FONT=arial]
So I thought well let's install iucode-tool:

[/FONT][/SIZE]```
[SIZE=2][FONT=arial]sudo apt install iucode-tool[/FONT][/SIZE]
```

More errors:

```

[SIZE=2][FONT=arial]Reading package lists... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]Building dependency tree       [/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading state information... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]iucode-tool is already the newest version (2.3.1-1).[/FONT][/SIZE]
[SIZE=2][FONT=arial]You might want to run 'apt --fix-broken install' to correct these.[/FONT][/SIZE]
[SIZE=2][FONT=arial]The following packages have unmet dependencies.[/FONT][/SIZE]
[SIZE=2][FONT=arial] intel-microcode:i386 : Depends: iucode-tool:i386 (>= 1.0) but it is not installable[/FONT][/SIZE]
[SIZE=2][FONT=arial] linux-image-generic : Depends: intel-microcode but it is not going to be installed[/FONT][/SIZE]
[SIZE=2][FONT=arial]E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
[/FONT][/SIZE]
```[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]Which was weird, but I followed the advice:

[/FONT][/SIZE]```
[SIZE=2][FONT=arial]sudo apt --fix-broken install[/FONT][/SIZE]
```

and got this helpful return:

```

[SIZE=2][FONT=arial]reading package lists... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]Building dependency tree[/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading state information... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]Correcting dependencies... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]The following additional packages will be installed:[/FONT][/SIZE]
[SIZE=2][FONT=arial]  intel-microcode[/FONT][/SIZE]
[SIZE=2][FONT=arial]The following packages will be REMOVED[/FONT][/SIZE]
[SIZE=2][FONT=arial]  intel-microcode:i386[/FONT][/SIZE]
[SIZE=2][FONT=arial]The following NEW packages will be installed[/FONT][/SIZE]
[SIZE=2][FONT=arial]  intel-microcode[/FONT][/SIZE]
[SIZE=2][FONT=arial]0 to upgrade, 1 to newly install, 1 to remove and 0 not to upgrade.[/FONT][/SIZE]
[SIZE=2][FONT=arial]1 not fully installed or removed.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Need to get 2,525 kB of archives.[/FONT][/SIZE]
[SIZE=2][FONT=arial]After this operation, 230 kB disk space will be freed.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Do you want to continue? [Y/n] y[/FONT][/SIZE]
[SIZE=2][FONT=arial]Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 intel-microcode amd64 3.20200609.0ubuntu0.20.04.2 [2,525 kB][/FONT][/SIZE]
[SIZE=2][FONT=arial]Fetched 2,525 kB in 0s (6,954 kB/s)       [/FONT][/SIZE]
[SIZE=2][FONT=arial]Selecting previously unselected package intel-microcode.[/FONT][/SIZE]
[SIZE=2][FONT=arial](Reading database ... 185600 files and directories currently installed.)[/FONT][/SIZE]
[SIZE=2][FONT=arial]Preparing to unpack .../intel-microcode_3.20200609.0ubuntu0.20.04.2_amd64[/FONT][/SIZE]
[SIZE=2][FONT=arial].deb ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]Unpacking intel-microcode (3.20200609.0ubuntu0.20.04.2) over (3.20200616.[/FONT][/SIZE]
[SIZE=2][FONT=arial]1) ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]Setting up intel-microcode (3.20200609.0ubuntu0.20.04.2) ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]update-initramfs: deferring update (trigger activated)[/FONT][/SIZE]
[SIZE=2][FONT=arial]intel-microcode: microcode will be updated at next boot[/FONT][/SIZE]
[SIZE=2][FONT=arial]Processing triggers for initramfs-tools (0.136ubuntu6.2) ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]update-initramfs: Generating /boot/initrd.img-5.4.0-40-generic[/FONT][/SIZE]
[SIZE=2][FONT=arial]I: The initramfs will attempt to resume from /dev/dm-2[/FONT][/SIZE]
[SIZE=2][FONT=arial]I: (/dev/mapper/vgregolith-swap_1)[/FONT][/SIZE]
[SIZE=2][FONT=arial]I: Set the RESUME variable to override this.
[/FONT][/SIZE]
```[SIZE=2][FONT=arial]

Unfortunately on reboot that not only made no difference to my wifi problem, but I don't think it worked to update the microcode.  If I try to install the downloaded microcode again I go through exactly the same error messages.  Of course the microcode error could be a red herring and have nothing to do with the wifi error...

Very grateful for any help anyone can offer.

[/FONT][/SIZE]

---

