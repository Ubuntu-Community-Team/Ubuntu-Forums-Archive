---
title: "Wireless gone with updates?"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by Mimsy on 2007-06-28
I installed a number of updates on my Feisty laptop last night, and when I started it this evening it would not connect to the wireless router. No big deal, I thought, that has happened before. I just need to reinstall the drivers. So I did that, the way it has always worked in the past, and nothing changed.

I did a search for similar situations here in the forum, and based on what I found typed "sudo ifconfig" in a terminal to see what it told me. My wireless interface, eth1, was not listed. I think that might be bad. I know it was alive and well last night... so what is it I am over-looking? Help would be very much appreciated! 

Thanks,
Mimsy

---

### Post by kevdog on 2007-06-28
Can you post the output of:

lshw - C network

Maybe this will tell us if your card is associated with any driver.

Also I have no idea what kind of card you are talking about, and what method you used to install the drivers -- madwifi, ndiswrapper, serialmonkey, etc.

---

### Post by Mimsy on 2007-06-28
Whops, sorry about that. [Compaq W200]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200") :) It's built into the lid of the laptop, which is very handy. The method in question has worked flawlessly in the past, so I don't think that's where the problem is. My theory is that something is preventing my installation from seeing either driver or card or both, but beyond there I am stuck.

Below are my terminal results, copied and pasted and transported to a working internet connection via USB drive. USB drives rule. :)

> mimsy@plaything:~$ lshw - C network
Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
            lshw -version

        -version        print program version (B.02.08.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )



---

### Post by kevdog on 2007-06-29
Weird,  I guess that command didnt produce too much useful output.  

How about just lspci.  I dont know why your network card didnt show up with the previous command.  Do you have to turn your network card on with this laptop -- Alt-F2 or something?? Or do you have to turn it on in the BIOS.

I dont want to see the entire output of lshw, but if you look at it, in any section is your wireless card listed???

---

### Post by Mimsy on 2007-06-29
Function-F2 normally turns the wireless card on and off, but tonight the little green light stays off no matter how much I press the buttons.

When I type in lspci I can see all other devices, including the winmodem I never bothered to configure, but not the wireless card.

---

### Post by kevdog on 2007-06-29
Im no genius, but I think you found your problem!! I have no idea how to fix it however.

---

### Post by Mimsy on 2007-06-29
At least I know what the problem is, which is a lot better than my situation was before I posted here. Thanks. :)

I'm thinking of completely removing the drivers for the W200 and installing them from scratch, just in case they went broken somehow.

---

### Post by Mimsy on 2007-06-29
That worked! I removed teh driver (in the simplest way possible, by deleting the whole folder) and reinstalled it, and now my laptop is happily wireless again.

---

