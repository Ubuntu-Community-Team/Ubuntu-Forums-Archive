---
title: "'modprobe ndiswrapper' fails"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by Mikulcak on 2005-11-02
Hello together,
when I try to get the ndiswrapper working with my T-Sinus 154 data, which is known as compatible, and type 

> sudo modprobe ndiswrapper

it says:

> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/misc/ndiswrapper.ko): Invalid argument

It's the third wireless-device I try to get to work with ndiswrapper 1.4, but the first to fail my efforts. So, it succeeded with two devices and I worked with them. But now it won't work,
help, I need somebody, help, not just anybody,
thank you,
Mikulcak

---

### Post by mxyzptlk on 2005-11-02
open a terminal

type ndiswrapper -l

there you will have the lis of ndis driver you have installed.

look if theres someone that says invalid driver, if so delete it

type ndiswrapper -e <drivername> 

and check if your driver and de device are there

try modprobe again

hope it helps

i said before in this forum that ndiswrapper is a powerful tool but it doesnt work with all devices.

try to find a linux driver and tell me

---

### Post by sopordave on 2006-12-20
I was having the same error when trying to 'modprobe ndiswrapper' with my Broadcom wireless card.  I fixed the problem by installing ndiswrapper-utils-1.8

hope this helps.

---

