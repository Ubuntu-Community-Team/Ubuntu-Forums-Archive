---
title: "Linksys WUSB Wireless"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by akathom on 2009-04-19
Here is where I am at. I loaded Ubuntu into my Dell desktop and what a joy, nice and easy. Now for getting on my wireless network. I have a Linksys WUSB100. Got all the information for my router I could find. Opened my network connections and it is enabled. Went to connections and wireless tab. nothing there. Clicked on add & editing window opens. Connect automatically is checked. I entered SSID, my network name. Mode infastructure is defaulted. Not sure if that is right. BSSIS - I have no idea what this is. I entered MAC address ie XX.XX.XX.XX.XX.XX which I assume I need. MTU is automatic. Security tab is none selected - no security for now on router. IPv4 setting - again have no idea. Does this make sense to anyone??? Is there somewhere I can link to to step me though all of this. I really no nothing about command prompts or how to get to them.Thanks

---

### Post by kiridude on 2009-04-19
ubuntu should see your wireless automatically, you shouldn't have to enter any info except your router password. if you right click the connection icon (with the computers), is the enable wireless checked? Did you check if the wireless is enabled on your computer?

---

### Post by tjwoosta on 2009-04-19
im a bit confused by your post as to what is happening

is your wireless card working, but you cant find any networks to connect to?

or is your wireless card not working at all?

or is it working and you can see networks, just not your own?


your post is just a little too vague for me to go from


type ifconfig in the terminal and see what interfaces are listed

for instance my wireless card is listed as wlan0, my ethernet card is listed as eth0, and the loopback interface is listed as lo

(your wireless might not necessarily be wlan0, sometimes they can be listed as ath0 or a few others depending on which drivers it uses)

if you dont see any wireless interfaces listed it could mean that you need to install the driver

this thread might help

[http://ubuntuforums.org/showthread.php?t=907809]("http://ubuntuforums.org/showthread.php?t=907809")

---

### Post by akathom on 2009-04-19
My networking is enabled and I find no wireless. I linked to the other thread which told me what driver I needed. I found the driver and downloaded it ( In windows due to the fact it finds my wireless ) but windows doesn't reconize the files. I reboot in Ubunto and it sees things just fine. I found all the text and read me pages ( all 29 pages ) and printed them , thank you that I don't need printer drivers. Now that I have all this information I have no clue how to input it. Being an ex windows user of 15 years a driver install was 3 clicks of the mouse. All this information must assume that I have an idea of how to do it. Can anyone help walk me though this???

---

### Post by kiridude on 2009-04-20
Here is a step by step on how to get things working for you: 

[http://ubunturt2870.pbwiki.com/FrontPage](http://ubunturt2870.pbwiki.com/FrontPage)

It seems that the drivers you need come included with Jaunty Jackalope (9.04) - the release candidate is out now and the final release is set for April 23rd. If you find the procedure for installing the drivers too complex, installing the 9.04 OS might be an easier solution for you.

---

### Post by akathom on 2009-04-20
And here I go again. I have just installed the 9.04 version and still did not find my network. Yes, it is enabled. I am on a desktop computer with a wireless USB device ( Linksys WUSB100 ) with a home wireless network which is all windows based right now. When I open my network for wireless it finds nothing there. I am asuming I will have to install the drivers through the terminal, although I haven't worked in anything like this in 35 years. I have downloaded the files but am not sure where they should be extracted to? I have downloaded the Ubuntu pocket guide and reference which I am going to start reading and hopefully understand. I haven't read 20 pages a year and this thing is 170 pages, fun is. All this make make, sudo, config is all greek to me. I am not about to quit as once I get through this I am hoping to not have any more problem until I start with my laptop after this. Please keep in mind that this is a dual boot system with Windows XP and the wireless is working on that side which rules out hardware problems. Thanks for any and all help.   Thom

---

### Post by kiridude on 2009-04-21
That's strange.

Well, I can suggest two ways:

1. Try ndiswrapper which uses your microsoft drivers in Linux.
2. Go through the compilation process with the drivers you've already got. This link has some good info:

[http://ubuntuforums.org/archive/index.php/t-1100594.html](http://ubuntuforums.org/archive/index.php/t-1100594.html)

This link will help you compile:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Now is a good opportunity to surpass your 20 read pages a year :razz:

---

### Post by akathom on 2009-04-22
I just wanted to thank everyone for their input. It has became quite obvious to me that this is next to impossible to set up without alot of reading on my part ( already read the pocket guide and reference ) and alot of trial and error. As I have 5 computer to try to connect to wireless I will be putting off switching them until I can get a better understanding of all this. After two weeks I have finally came to the realization that I think I have to change the information in the Makefile but am not sure how to or to what. The manual really didn't go into this make and configure and compiling stuff so until I can become more of an expert I will just try thing on my own for a while. It seems to me that Linux users seem to forget that ex Windows users really have no clue on alot of this. As I said, Thank You everyone for all the help and support and I hope to be back soon as less on a newbe.

---

### Post by Methuselah on 2009-04-22
I also have jaunty RC installed on a computer and it doesn't see the wireless...but I am able to connect manually by editing configuration files.
What I haven't figured out, is why Network Manager isn't working.

---

### Post by abyssius on 2009-04-22
> It seems to me that Linux users seem to forget that ex Windows users really have no clue on alot of this.
It's unfortunate that akathom has the impression that what he had to go through is a necessary procedure. The truth is that his particular problem is actually unusual. I have a Linksys WUSB adapter (although a different model than akathom's). I got it to work very easily using ndisgtk + windows driver with 8.04. When I upgraded to 8.10 the same adapter immediately worked without any need for intervention on my part (no need for ndisgtk or windows drivers). This was also the case for 9.04. 

Akathom should realize that even though he had this problem, wireless simply works for the majority of users. Of course, you won't here this, because no-one usually goes on a support forum to report that they didn't have to do anything to achieve wireless connectivity.  

I've gotten several different wireless adapters, PCI, USB, integrated (some quite old) to work without ever having to compile drivers, etc.

@ Methuselah
I've gotten into the habit of ignoring network manager, and setting up wireless connections simply by defining them in the 'interfaces' file. This is actually way easier than Windows, especially with some adapters where you have to waste resources by running the adapter's "utility" in RAM every time you boot up Windows.

---

