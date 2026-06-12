---
title: "jsymphonic: Invalid OMGAUDIO directory?"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by disastrophe on 2010-06-30
Hello, I am a very new convert to Linux and I love it! I started off with a Lucid/vista dual boot and a couple of weeks later gave the vista space to another Ubuntu install, seemed like a good idea as I really don't know what I'm doing yet - but I am teachable lol.
Anyway I am having a rather bewildering struggle with jsymphonic, not even really sure if I need it since Ubuntu seems to be able to see my walkman just fine, although I haven't tried writing to it yet, I'm kind of afraid of messing something up and locking myself out.
So, I installed jsymphonic via synaptic and on the first run of the program it asks me to specify the device path which I believe is /dev/sdf1, after which it immediately shut down with an obvious error. I ran it again from a terminal and here is the output:
```
Jun 29, 2010 8:22:53 PM org.danizmax.jsymphonic.gui.SettingsHandler startDocument
INFO: Reading file /home/anton/.jsymphonic.xml...!
Jun 29, 2010 8:22:53 PM org.danizmax.jsymphonic.gui.SettingsHandler endDocument
INFO: Done reading file
29 Jun 2010 20:22:53 [INFO]    org.danizmax.jsymphonic.gui.JSymphonicWindow:<init> : Initializing JSymphonic...
29 Jun 2010 20:22:54 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:mountDevice : Mounting the device "sdf1"
29 Jun 2010 20:22:54 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
29 Jun 2010 20:22:54 [WARNING] org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : The device path /dev/sdf1/esys does not exist!
29 Jun 2010 20:22:54 [SEVERE]  org.naurd.media.jsymphonic.device.sony.nw.NWEsys:<init> : Invalid OMGAUDIO directory.
Exiting program.
```Hmmm, well that doesn't sound terrific. Anybody have any insights? Or would it be okay to just use Nautilus? Worked with exploder when I was using windoze. Any help will be very much appreciated, thank you.

---

### Post by hundovir on 2010-11-12
Hello! I've only just started using Xubuntu after years of windows, so have only just seen your post. I have Jsymphonic installed on my walkman itself. This was recommended in the docs because it makes the whole thing portable - and indeed, even though I installed on windows(xp), it now runs on Xubuntu. the device path is thus just ".." (without quotes.) Don't know if that might help.

Unfortunately i had forgotten that on my particular walkman (nw-a805) the dat files in OMGAUDIO need to have all uppercase names. Jsymphonic writes them all lowercase whenever it updates the files. However, I dont seem to be able to rename them to uppercase - I keep getting "file already exists" errors when using rename. I'll suss it out eventually I suppose!

Edit: workaround for my prob - copy the .dat files back to the computer, rename them to uppercase, copy them back to the walkman! Clunky, but it works!

---

### Post by jeyasooriya on 2013-03-29
I have just installed jsymphonic.  I am not able to connect network walkman NW-5003.  for the reason cannot found  OMAUDIO  folder. I am new to ubunto. Please give advise to solve .

---

