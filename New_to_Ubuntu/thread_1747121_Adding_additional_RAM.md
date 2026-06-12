---
title: "Adding additional RAM?"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Bobrm2 on 2011-05-02
How do I find out if I have any empty RAM slots? Thanks

---

### Post by wolfen69 on 2011-05-02
Open the computer and look. 

Besides that, go into the BIOS and it will tell you how many are being used.

---

### Post by Bobrm2 on 2011-05-02
I hoped there is a terminal command that would give me all the necessary information, about this old box. Thanks anyway.

Bob

---

### Post by QLee on 2011-05-02
Well, you probably already know how much RAM your system now has, ...or you could use the command, free -m to show memory in your system in megabytes, or perhaps -g to show in gigabytes.

Consult the documentation for your system to see the specs, that will list how many slots are on the Mainboard and you can probably determine from that the likely configuration. If you no longer have the documentation, use your favourite search engine to find it on the manufacturer's website. ...or go to a memory sales site (for example Crucial) and enter your system model number, your system is probably in their database and it would show you the number of slots and the specs of the necessary memory for it.

I like the idea of looking at the BIOS as suggested by wolfen69, likely you'd find what you need just by doing that the next time you boot. If this is a laptop, there's likely a "door" to the memory area on the bottom of the case if it is upgradeable.

---

### Post by Wolligog on 2011-05-02
you can find out from this site exactly what type of RAM you need and how much your pc will take

[http://www.offtek.co.uk/](http://www.offtek.co.uk/)

found it rather helpful for when i wanted to upgrade myself

---

### Post by oldfred on 2011-05-02
This shows memory:
sudo lshw | grep -m 1 -A 25 "*-memory"

You can make a HTML version with everything.

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
udevadm info --export-db > file.txt

---

### Post by Bobrm2 on 2011-05-02
This all great and I've learned a lot arriving at a conclusion that I have an empty DIMM DDR2 slot, and I can increase my RAM by 512 megs. which I intend to do; but after I figure out why/what is dragging this system down.

  Had run into "Top" "Free (-M}". I don't know how you guys keep all these commands in your head, which would make life much easier (using the terminal that is).  Headed for [http://www.offtek.co.uk/](http://www.offtek.co.uk/)
shortly.

  Now to try and determine which is the memory hog, or if the system just needs a shot of B-12 or some "Low-T". 

   Thanks once more. 
Bob R

---

