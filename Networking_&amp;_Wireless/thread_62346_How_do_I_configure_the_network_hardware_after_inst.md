---
title: "How do I configure the network hardware after install?"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by docbill on 2005-09-04
Durring install I did not know I needed to reset my card to non-PNP mode and use the eepro module option autodetect=1.  Now I do, and I can get the live CD to recognize my network.  However, I can not find any tool on my installed machine to configure network.  I did find two network tools in the menu.  One only shows loopback and has no options to create another type of hardware.  The other asks for my password, when I enter it the window closes and nothing else ever appears.

Bill

---

### Post by s_p_a_r_k_y on 2005-09-04
from the command line 
```
 lsmod 
```
does that show the eepro module being loaded?
If not 
```
sudo modprobe eepro
``` and add your options. Then ```
ifconfig
``` and see if it has an eth0 device

---

### Post by docbill on 2005-09-05
Sparky,  if you don't know.  Then don't respond.  

I am looking for a way to run a configuration program like the one included in the installer.  In general it is a bad idea to manually do steps in a distribution as often the break the GUI programs that should do it automatically.  Besides that, your steps won't work for the following reasons:

1. I mentioned the autodetect=1 option is needed for eepro with an EthernetExpresss Pro+ 10 ISA card.
2. Even when the modual is loaded, the eth0 device is still not recognized.  

Here is what I tried as command line:

1. Add eepro to /etc/models
2. Created an the appropraite file in /etc/models.d to load eepro with
    the autodetect option.
3. Reboot
4. Try ifup on eth0 to find eth0 is still not recognize.

In the old days, it use to be neccessary to add eth0 to /etc/modules.conf to correctly map it to the network device.  I am guessing something like this is still need, but there is no /etc/modules.conf file.

I did verify in the proc file system that the eepro is correctly mapping to IO port 210.  For some reason irq 7 is not getting mapped to eepro, but if I remember correctly irq mapping is not essiential.

As I said, loading eepro module in the live CD in the expert boot menu with the autodetect=1 option works.  But I can not find a program in the installed system for doing the same thing.  I finally, took the brute force method and reinstalled the whole OS just so it would pickup the correct network configuration from the installer program.  However, I am building this system for a 11 year old, with parents that know nothing about computers.

If there isn't a simple GUI way for them to do these things, then this obviously is not the right Linux distribution for me to use.

So, is there a way to setup the network including hardware on a pre-installed system.

Bill

---

### Post by s_p_a_r_k_y on 2005-09-05
wow whats with the hostility there? I'm trying to help, one does this by asking questions to see where the problem "could" lie. From your description I wasn't sure where the problem was lying. However debugging is a commonly used practice to locate where the problem lies. Sorry if my trying to help has offended you. I believe I can help but need you to work with me. I have found that in debugging GUI's don't help at all, although they are easier to use, even on windows I use the command line to do real debugging. So you can either try to work with me and I will be glad to help or complain about my asking questions to help in the debugging process

---

### Post by docbill on 2005-09-06
Sorry.  I did not intend to sound hostile.  What I should have said is:  Wouldn't it be better to reply with the URL of the Linux networking howto, if your answer is just a subset of it?  What I was hopping for is ubuntu specific information.

It turns out the program I need to run is network-admin.  However, something in the ubuntu configuration is broken, so none of the System->Administration tools will open.  The work around is to open a non-root terminal and type:

xhost +
su root network-admin

It looks like this program does not handle real low hardware stuff, but once the correct module is loaded with the correct options it will handle the rest.

So in my case I still had to do the following steps manually:

modprobe eepro io=0x220 irq=10

this loads the module only for the current boot.  To make it load on 
the next reboot, the following commands are needed:

echo eepro >> /etc/modules
echo options eepro io=0x220 irq=10>>/etc/modprobe.d/eepro.modules

Bill


[QUOTE=s_p_a_r_k_y]wow whats with the hostility there? I'm trying to help, one does this by asking questions to see where the problem "could" lie. From your description I wasn't sure where the problem was lying. However debugging is a commonly used practice to locate where the problem lies. Sorry if my trying to help has offended you. I believe I can help but need you to work with me. I have found that in debugging GUI's don't help at all, although they are easier to use, even on windows I use the command line to do real debugging. So you can either try to work with me and I will be glad to help or complain about my asking questions to help in the debugging process[/QUOTE]

---

