---
title: "Ubuntu 8.10 to Ubuntu Studio 8.04"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by toothdecay on 2008-12-29
So I'd like to use the real time kernel for audio work.

As I understand the latest real time kernel is not recommended.

I'm currently using Ubuntu 8.10 Intrepid and would like to give Ubuntu Studio 8.04 hardy a whirl for the working real time kernel.

I have a separate /home partition and would like to keep all of the data on the intact and possibly keep some app settings intact so I dont have to add my mail accounts, address book to Thunderbird for example.

I guess what I'm asking is what will happen if I install Ubuntu Studio and keep my /home partition?

---

### Post by adult swim on 2008-12-29
whenever you are installing 8.04 when you get to partitioning select manual.  then choose your root partition and select it to be mounted as / 
then select your home partition and select it to be mounted as /home.  make sure that the format box is NOT checked.  continue on with the installation and everything should be fine.
once youve done this when you boot up 8.04 studio it should have all of the config files for the programs that you have used under 8.10 already there and most of your settings will still be intact.

---

### Post by toothdecay on 2008-12-29
Thank you! This is what I was hoping to hear! :D

---

