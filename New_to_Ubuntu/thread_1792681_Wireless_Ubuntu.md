---
title: "Wireless Ubuntu"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Sothatshowudoit on 2011-06-28
I have tried to get into linux & Ubuntu but finitially fell at the hurdle of finding something that invites you to click on it to download. I eventually managed to download and install Ubuntu or so I thought and it does run but I cannot get it to connect to the internet yet  notebook  will run & connect on the  original SuzeLinuxEnterprize .  Everytime I click the Ubuntu wireless icon to connect wireless I get the message back "network now disconnected" it wasn't ever connected!   I am thinking its a corrupted install but how do you delete or repair it please? :confused:

Hope some of you good people can help me get this operating system in place so that I can start to get the hang of it. Cheers

---

### Post by ratcheer on 2011-06-28
Please post the output of "sudo lspci -v".

Tim

---

### Post by Sothatshowudoit on 2011-06-30
Hi Tim

Thanks for reply, Had a problem with booting the Ubuntu but now cleared hence delay, looked but cannot find any reference to Sudo Ispc-v.
Where do I find this?  

Thanks

Den

---

### Post by dFlyer on 2011-06-30
It's sudo lspci -v

You will be required to provide you password provide your running Ubuntu.

---

### Post by Sothatshowudoit on 2011-06-30
Hi Gary, yes realised that just after I pressed the submit but where do i find its output?

Thanks

Den

---

### Post by dFlyer on 2011-06-30
The out put should have been displayed on the terminal you entered the command from.

---

### Post by Sothatshowudoit on 2011-06-30
I dont really enter a command i have option to start in Ubuntu or Linux and it does the rest. I did run Checkbox and it confirms Broadcom BCM4312 802.11 a/b/g rev 2 ok but then also confirms no internet connection?

---

### Post by ratcheer on 2011-06-30
Ok, we are trying to help you, but it is like you are refusing to be helped. Run application "Terminal" and enter that command at the prompt in the terminal window. Then copy the output from the same window and paste it into a reply to this thread.

Tim

---

### Post by computerandu on 2011-06-30
> **Sothatshowudoit said:**
> I dont really enter a command i have option to start in Ubuntu or Linux and it does the rest. I did run Checkbox and it confirms Broadcom BCM4312 802.11 a/b/g rev 2 ok but then also confirms no internet connection?

When someone asks for output it mean you have to open the terminal (ctrl+alt+t) and then type the command there..

for wireless problem with broadcom you might want to check at [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

### Post by Sothatshowudoit on 2011-06-30
Thanks guys, I didn't know about Terminal, I'm totally new to all this. Tried "sudo Ispci-v" with and without quotes from the prompt drs@notebook:-$ and it gives   drs@notebook:-$

Explain as the Ubuntu notebook cannot connect to the internet (the underlying problem) I am therefore using a separate windows PC to liaise with the forum and I'm not aware of a way to copy/ paste/connect to the notebook directly. Sorry for my lack of Ubuntu/Linux awareness. I guess the output may not be what you were expecting so have I still not got it right?

---

### Post by dFlyer on 2011-06-30
Its:

sudo lspci -v

No caps and you need a space between i and -v

---

### Post by Sothatshowudoit on 2011-06-30
Cheers that worked & figured way to copy into .odt doc and transfered by flash drive.



Subsystem: Broadcom Corporation Device 969c  
 	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16  
 	Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]  
 	Capabilities: [48] Power Management version 2  
 	Capabilities: [50] Vital Product Data <?>  
 	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-  
 	Kernel driver in use: tg3  
 	Kernel modules: tg3  
 

 80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)  
 	Subsystem: Hewlett-Packard Company Device 3030  
 	Flags: bus master, fast devsel, latency 0, IRQ 17  
 	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]  
 	Capabilities: [50] Power Management version 2  
 	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-  
 	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00  
 	Capabilities: [100] Virtual Channel <?>  
 	Kernel driver in use: HDA Intel  
 	Kernel modules: snd-hda-intel

---

### Post by wildmanne39 on 2011-06-30
Hi, you should be able to connect that laptop to a wired connection and run the commands and output the results here. If your card is a broadcom 4312 this link should get you fixed up. You will need to connect to a wired connection.
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by Sothatshowudoit on 2011-07-01
Thanks wildmanne39 and all below - Results so far, 



Can connect wired but not wireless which is what i am hoping to achieve.
Tried Wildmanne39 suggestions many thanks, will go on with other steps but just ask given results of 1 & 2 if they are still the direction to travel? I also have Suze Linux Enterprize as the supplied original system on purchase so guess there is a Linux based wireless driver as the wireless works on that albeit not so keen on SLE hence trying to move to Ubuntu. Appreciate everyones help with this, sorry I am old & slow but keen to learn. 



Step 1 result:
 

 W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb) 
   Could not resolve ‘gb.archive.ubuntu.com’  
 

 

 W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-2ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-2ubuntu1_all.deb) 
   Could not resolve ‘gb.archive.ubuntu.com’  
 

 

 W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) 
   Could not resolve ‘gb.archive.ubuntu.com’  
 

 

 W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb) 
   Could not resolve ‘gb.archive.ubuntu.com’  
 

 

 

 Step 2 result:
 SystemError: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb) Could not resolve 'gb.archive.ubuntu.com'

---

### Post by wildmanne39 on 2011-07-01
Hi, was that all the information that was given?
run this command in the terminal
```
lspci -nn
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by gordintoronto on 2011-07-01
When connected by an Ethernet wire, run "software sources" and select "main server." It will prompt you to reload, do it. Then exit and..

Run Additional Drivers, and it should offer you the Broadcom driver. Activate it.

---

