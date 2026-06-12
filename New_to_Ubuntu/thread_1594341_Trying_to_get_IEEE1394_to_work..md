---
title: "Trying to get IEEE1394 to work."
date: 2010-10-12
forum: New to Ubuntu
---

### Post by EddInaBox on 2010-10-12
I have a Toshiba Tecra M10, and wish to connect a Sony mini DV camcorder.  Despite several months of trying on and off I have got nowhere, I hoped updating to 10.10, which apparently has the new Firewire stack as the default would sort it out, but no joy.

I have installed Kino and dvgrab, and launched them from the terminal using gksu and sudo, but just get error messages to the effect that no camera is detected.  The `AV/C Device´ box on the IEEE 1394 tab in Kino's preferences is blank.

lspci gives:
...
06:0b.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
06:0b.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
...

lsmod|egrep 'firewire|1394' gives:
firewire_sbp2          12767  0 
firewire_ohci          21106  0 
firewire_core          46643  2 firewire_sbp2,firewire_ohci
crc_itu_t               1383  1 firewire_core


I have searched the forum here and the net in general and tried all sorts of things that I probably shouldn't, since I don't really have much idea what I'm doing, so any help would be gratefully received.

---

### Post by seventhsamurai on 2010-10-12
I have had similar issues with my JVC Mini DV camera. My firewire ports work fine with external hard drives but do not detect these video cameras. Perhaps a driver issue? It would be nice to know which cameras are compatible.

---

### Post by EddInaBox on 2010-10-13
I can't even get my Firewire HDD to work, but I've read a bit about this sort of problem and I might be able to give you some pointers.  What version of Ubuntu are you using?  If you install Kino and launch it from terminal by typing ‘gksu kino’ do you get any further?

---

### Post by EddInaBox on 2010-10-16
I have now resolved my problem with some help from elsewhere, in case it is of use to anyone else, I typed 

tail -f /var/log/kern.log

into terminal and this showed that the IEEE1394 was working with my  external drive, but not with the camcorder (which uses a different cable), this lead me to suspect my  new cable and I purchased another one, my camcorder now shows up in  Ubuntu as it should.

---

### Post by tedrickenator on 2010-10-26
I am not able to get kino to work on on firewire on the mac mini - I get the error:

WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!

---

### Post by marx321_10 on 2010-10-26
I had the same problem with kino and my old camcorder. So I went to terminal and typed sudo kino and went it started it fixed the problem. I can't remember but it had something to do with loading a module and having permission. Hope this helps.

---

### Post by Duanegerous on 2010-11-16
I had a similar problem.  I followed the information in the various posts above to get the raw1394 module loaded, but still received the Kino error message :

WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394

verified the module was loaded using 

lsmod

turns out my problem was the /dev/raw1394 was not globally read-writeable, so I changed the permissions

sudo chmod o+rw /dev/raw1394


now I can capture video from my Sony miniDV camera using Kino. YAY!

---

