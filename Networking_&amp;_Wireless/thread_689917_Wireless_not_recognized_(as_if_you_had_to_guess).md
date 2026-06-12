---
title: "Wireless not recognized (as if you had to guess)"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by Tssabackus on 2008-02-06
My computer informs me i have a Realtek RTL8185 54M Wireless Lan Network Adaptor, and i have a Dlink ANT24-0400 sma attached to it. Thats my antenna. The thing is, i don't have internet while in ubuntu,no wired...so i would need instructions for offline downloading and installation. I could get wired, but its just a big hassle so I would only do that if I knew the proposed solution would work.

Thanks for taking a look at this!

---

### Post by pytheas22 on 2008-02-06
There is a Linux driver for that card supplied by the vendor at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L) .

Download the driver on a computer that has Internet access, move it to your Ubuntu machine and unpack the tarball.  There is a readme file inside it that explains how to install it.

Note that before you attempt to compile and install the driver you will need to get a compiler and things installed on your system: put your Ubuntu installation CD in your drive and in a terminal type:
```

sudo apt-get install build-essential
```

---

### Post by FleetAdmiral74 on 2008-02-06
Alright, so he does not need to add the CD as a repo? I think i remember having to do that before...but maybe its added be default now?

I see some instructions from the readme file here, 

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )

I dont under stand this second part though...we type in ./wlan0up and ...the parentheses appear? Hehe, kinda technical for me, which means he will have no idea how to finish it. Can anyone dumb this down for me? :)

---

### Post by pytheas22 on 2008-02-06
> he does not need to add the CD as a repo

Yes, in 7.10 I believe that the CD is automatically set up as a repository.  You could check using the Settings>Repositories dialog in Synaptic.

> (2)Load the driver module to kernel and start up nic
./wlan0up
(if "insmod: error inserting 'r8180.ko': -File exists." met,
./wlan0rmv
./wlan0down
./wlan0up
should be OK.
)

These commands are just scripts, and all they do is insert and remove the module using standard commands.  Open the wlan0rmv and wlan0up files in gedit to see what commands are actually being entered.  I guess the readme is confusing, but basically I would just type ./wlan0up to load the module and put the interface up, because that's all that script does (using insmod and ifconfig commands), and wlan0rmv and wlan0down take it down.

I also noticed that the makedrv script doesn't include a "make install" command.  Maybe this doesn't matter, but if you have problems you should probably run ./makedrv again, and then run the command

```
sudo make install
```

immediately after.

---

### Post by FleetAdmiral74 on 2008-02-07
ok, we shall give it a try and I'll report back.

---

