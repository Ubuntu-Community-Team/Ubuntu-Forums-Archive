---
title: "LTSP Thin Client Wont Boot"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by dfault312 on 2008-01-07
I just finished re-doing my thin client setup. I have a fresh install of Ubuntu 7.10 on the server, and then installed LTSP and setup a thin client following the LTSP Quick Install instructions. The last time I had this working, that's all I remember doing, except that the server didnt have a fresh install and was running 7.04. Now when I try to PXE boot the thin client, it displays the mac address, then says DHCP....../ for a little while, until it says 

> PXE-E51: No DHCP or BOOTP offers recieved

I searched the forums, and google, and I havent been able to find anyone else with this error. Google had one result, but it was someone trying to boot NT off a hard drive and using PXE accidentally. Can anyone help?

---

### Post by dfault312 on 2008-01-07
I tried restarting the DHCP server but it failed to stop, and failed to start. So I'm guessing I need to get DHCP working... but I'm not sure how. Also, I have two network cards in my server (eth0, and etc1) I remember having one set up with a static IP before, but I can't figure out how they are supposed to be setup now.

Update: I accidentally skipped the first step in the [Quick Install]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall"), which was setting up the ethernet cards... so I did that, and then ran > sudo ltsp-update-sshkeys

but im still getting the same error.

---

### Post by dfault312 on 2008-01-07
Ok, restarting worked this time. I keep missing little details. Sorry about that. Anyway, it still won't boot. I get to the Ubuntu splash screen, but once the bar loads, all I get is a blinking cursor.

---

### Post by jefflawr on 2008-01-07
hi mon,

Coincidentally, I had the same problem today, and my solution might help you, too. 

Some background: I've been trying to set up a class network in my spare time (ha!) for the last couple of months. My goal is eventually to have both thin and fat clients running (the typing tutor is glacial on a thin client, but should be okay if using local ram and video card).

The secret nobody ever mentioned to me (too obvious to true weenies, probabaly) is that there are (at least) two dhcpd.conf files.

I read that for ltsp to work, I needed to uncomment the line, 
# authoritative;

All you have to invoke the cursed blinking cursor is uncomment it in /etc/dhcp3/dhcpd.conf 

The other file, that is the one that governs thin client booting, seems to be 
/etc/ltsp/dhcpd.conf

I only figured this out because my thin client booted with an IP address outside the range I specified in that first file. In any it  worked for me to edit the files as follows:

/etc/dhcp3/dhcpd.conf
- comment out the "authoritative;" line - make sure it starts with a '#' character

/etc/ltsp/dhcpd.conf 
- uncomment the "authoritative;" line by deleting the leading '#' character, if any on that line
- specify any IP range you want for thin clients in this file, as described elsewhere

For tastier results, don't forget to restart the dhcp3-server:
/etc/init.d/dhcp3-server restart

Sorry so long, but I wanted to be clear. If you get any clarity on how to add fat clients that use local RAM and CPU, please advise!

Best 
JML

---

### Post by dfault312 on 2008-01-08
thanks! i tried that. it didnt work. if anyone has any other suggestions, please advise!

---

### Post by jefflawr on 2008-01-12
Hey dfault -- 

I think my "authoritative" line solution was a fluke, since the lan started flaking out on me shortly after I posted it (without doing any more tinkering, either). I next tried several fresh installations and got different weirdness with each install.  I couldn't even repeat my errors, and was suffering quirkiness much like those described here: 
[http://ubuntuforums.org/archive/index.php/t-489970.html](http://ubuntuforums.org/archive/index.php/t-489970.html)

Since some of my installations flamed out with installation errors, I tried the following end-run around the problem:
1. I downloaded a fresh iso and burned a new installation CD at a slow burn 
2. I started using a thin client and monitor I knew to be reliable to test function.

Now, it works as advertised (knock on wood). 

Good luck and sorry about the misleading "solution" - I was feeling your pain and thought I had it fixed. 

Jeff

Good luck,
Jeff

---

### Post by dfault312 on 2008-01-12
I turned off my splash screen to get more details about what was happening when I was booting up. Turns out that my sound card wasn't cooperating, so I opened up /var/lib/tftpboot/ltsp/i386/lts.conf to turn off sound for the client and found that it was blank. I did a google search to find the proper format, and eventually ended up with the following configuration of lts.conf that fixed my problem.

> [default]
    X_COLOR_DEPTH=24
    LOCALDEV=True
    SOUND=True
    NBD_SWAP=True
    SYSLOG_HOST=server
    XKBLAYOUT=us

---

### Post by marioquark on 2008-03-17
> **dfault312 said:**
> Ok, restarting worked this time. I keep missing little details. Sorry about that. Anyway, it still won't boot. I get to the Ubuntu splash screen, but once the bar loads, all I get is a blinking cursor.

can you tell us what are the "little details"?

---

