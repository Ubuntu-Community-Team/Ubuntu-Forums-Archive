---
title: "Is there any way to get Ubuntu to detect my SD card reader?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by st4 on 2009-04-28
I just got a card reader and Ubuntu won't detect it, please help.:(

BTW, It doesn't say anywhere that it's linux compatible. Can I still use it? Thanks

---

### Post by Sef on 2009-04-28
1) What make and model is your card reader?  

2) What version of Ubuntu do you have?

3) How is it connected: external or internal?

---

### Post by st4 on 2009-04-28
> **Sef said:**
> 1) What make and model is your card reader?  

2) What version of Ubuntu do you have?

3) How is it connected: external or internal?Thanks for the reply.

1. It's [this one.]("http://www.amazon.com/Memory-Card-Reader-USB-2-0/dp/B000R4J1G8/ref=sr_1_1?ie=UTF8&s=electronics&qid=1240579652&sr=1-1")

2. I just d/led Ubuntu 9.04 this morning.

3. I guess it's external, it connects to the pc via usb.

---

### Post by llamabr on 2009-04-28
It should just work.  What happens when you plug it in?  And also, post the last 10 or so lines of dmesg, right after you plug it in.

---

### Post by st4 on 2009-04-28
> **llamabr said:**
> It should just work.  What happens when you plug it in?  And also, post the last 10 or so lines of dmesg, right after you plug it in.This is why I'm posting in Absolute Beginner Talk: what is dmesg, is that a line command I need to put in the terminal?

And nothing happens when I plug it in, that's the problem.:(

---

### Post by llamabr on 2009-04-28
Sorry.  Plug it in, wait 10 seconds, then in terminal, run this command:

```
dmesg | tail -10

```
And post the output

---

### Post by st4 on 2009-04-28
This is a response to your previous post, I haven't run the command yet. But [this]("http://i183.photobucket.com/albums/x71/fst4wfloyd/cardreaderpic.jpg?t=1240961030") is what appears on my desktop when I plug the card reader in. I've never used a card reader before, so can you tell me what I do with that?

---

### Post by st4 on 2009-04-28
> **llamabr said:**
> Sorry.  Plug it in, wait 10 seconds, then in terminal, run this command:

```
dmesg | tail -10

```
And post the outputThis is what I got from that command,

bill@bill-desktop:~$ dmesg | tail -10
[ 3857.830048] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=352 TOS=0x00 PREC=0x00 TTL=255 ID=34930 PROTO=UDP SPT=67 DPT=68 LEN=332 
[ 3864.160542] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=352 TOS=0x00 PREC=0x00 TTL=255 ID=34968 PROTO=UDP SPT=67 DPT=68 LEN=332 
[ 3876.541116] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=352 TOS=0x00 PREC=0x00 TTL=255 ID=35011 PROTO=UDP SPT=67 DPT=68 LEN=332 
[ 3878.687112] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35024 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3878.735162] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35025 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3882.682816] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35037 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3882.755366] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35040 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3886.704006] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35050 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3886.750108] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35051 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3893.018017] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=352 TOS=0x00 PREC=0x00 TTL=255 ID=35071 PROTO=UDP SPT=67 DPT=68 LEN=332 
bill@bill-desktop:~$

---

### Post by llamabr on 2009-04-28
> **st4 said:**
> This is a response to your previous post, I haven't run the command yet. But [this]("http://i183.photobucket.com/albums/x71/fst4wfloyd/cardreaderpic.jpg?t=1240961030") is what appears on my desktop when I plug the card reader in. I've never used a card reader before, so can you tell me what I do with that?

Awesome.  What do you think a card reader does?

---

### Post by st4 on 2009-04-28
> **llamabr said:**
> Awesome.  What do you think a card reader does?Well, I browsed that folder, and I thought i had some pictures in it. But I can't find any.

---

### Post by st4 on 2009-04-28
Okay, I finally figured out how to get pics to my pc.:o Thanks for the help, llamabr, and your patience.

---

