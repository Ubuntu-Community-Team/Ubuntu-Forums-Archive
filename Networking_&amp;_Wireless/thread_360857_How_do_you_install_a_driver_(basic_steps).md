---
title: "How do you install a driver? (basic steps)"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by Ethelbert2 on 2007-02-13
[FONT="Georgia"][SIZE="3"]I am very new to Linux- just experimenting with an old p3 with 600MB of ram - I am dual booting with XP SP2 which works fine and finds a wireless card I have and connects to an Orange broadband router. (It took some trouble to get there but eventually that and two other computers now work.)

I have already discovered that actually connecting with the Internet is one of the still frustrating elements of Linux (whether wireless or modem) and I am not so clear about it.

But I loaded the new Ubuntu 6.10 alongside Win XP. Small problems - it kept freezing in the graphical loading and so I had to install it in text only. The same happened with 6.06. (This may be relevant).  Now seems fine.

It too finds the card and lists it in Network Manager. It has a Realtek chipset. I tried filling in the details of my router and enabling it but nothing happened. I ticked the box alongside it (seemed a rational thing to do since there was a box there). Everything froze solid. I had to reboot and the same happened again three times.

I assume therefore that despite showing it, Linux has not really "got" this PCI wireless card. So in the device section I listed it and although the chipset is named etc much of the information says "device unknown", "device type unkown" and "capabilities unknown" etc etc.

I asume from reading around that this means something about the driver or its absence.

Back in Win XP I spent a lot of time chasing around and eventually located a newly released Linux driver for the chipset from Realtech (chipset seems to be rtl8185). (The link to that lucky bit of information is surecom-forums.no-ip.biz:8001/auth/phpbb2/viewtopic.php?p=8100&sid=9903ba99435341756a4dfcc04fb7d2f6 
incidentally.)  (Or the driver page which is here  --- realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352

I had been chasing the Windows driver and was going to use the NDISwrapper though I have no idea how you actually install it or the drivers you need. But instead of asking that   
I guess the direct Linux driver is better.

But I have no idea either how to go about installing this driver I have downloaded. I can put it on a floppy but how do I get the Linux system to go there, find the driver and put it into place.? Where must I put it and how do you do that (either GUI or command line - I simply do not know where to begin)? What do you have to do then?

May I make a plea as a beginer - plenty of advice in forums is very knowing and short cirucits basic instructions,. saying things like "unwrap your gz and navigate to the installation file" and so forth. I am a BEGINNER. I don't know how to do those things, or where the installation file it or what it is,  and when I ask for advice I need very basic guidance. 

(Incidentaly I like the look of Ubuntu and am tempted - but even In XP (which finds a lot of stuff for you) wirless was not so simple.  For those of you keen to draw us outsiders in - please don't insist we have to be "clever or you won't help us" - because that way we shall never be won over.

Anyway I hope someone can make sense of my inquiry - how to install a driver and would be grateful for any advice.[/SIZE][/FONT]

---

### Post by Floppyjoe on 2007-02-13
The first link you have there is a tutorial for installing your driver. You will need to use the terminal to enter those commands. Click on Applications/Accessories/Terminal to open a terminal. 

Copy those commands one at a time to the terminal. You need to leave out the # part though. That is just there to indicate a command prompt.

You will also need to follow the instructions that came with your driver as is mentioned in the tutorial.They are probably in a readme file.

You may need to change to the /root/rtl8185l directory to run the tar command by doing the following at the command promt in the terminal:
```
cd /root/rtl8185l
```

Good luck with that.

---

### Post by Ethelbert2 on 2007-02-14
[COLOR="DarkOliveGreen"][FONT="Georgia"]Many thanks for such a prompt and trouble taking reply - yes there is a read me which more or less says the same as the other forum link but in a little more detail. But I still have some confusion here.

Here is what it says is in the file:[/FONT][/COLOR]

[COLOR="DarkOrange"]The driver is composed of several parts:
    (1)source code
	r818x.tar.gz
	stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
	wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
	wpa_supplicant-0.3.8.tar.gz
    	
    (6)Example of supplicant configuration file
	wpa1.conf[/COLOR]

[COLOR="DarkOliveGreen"][FONT="Georgia"]This is *fairly* clear I agree. Then it says what to do, which may be clear but presupposes some confidence with Linux which is where I fall down and where I usually find the Linux forums very unsympathetic with lots of "if you can't even grasp that then huh!!" type of comments.

It says [/FONT][/COLOR]
[COLOR="DarkOrange"]
< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )[/COLOR]

[COLOR="DarkOliveGreen"][FONT="Georgia"]Of course 
"running the script" is seemingly simple but ----
on instruction no 1 for example - do I just enter that as an instruction in the command line? But then is that enough? Should I have put the files somewhere first? ie on a floppy or copied them somewhere etc?

Do I have to get them out in some way? etc etc.

No 2  Load to the module etc - I assume the script just does it but do I have to do anything first by going to certain directories etc?  And the brackets bit is confusing.

PLease excuse me labouring the points and demanding what might seem excessive  handholding but it is the little missing bits that are important here. 

But let me also say I do appreciate it if *anyone* takes the trouble to answer [/FONT][/COLOR]

---

### Post by Ethelbert2 on 2007-02-14
[COLOR="SeaGreen"][SIZE="3"][FONT="Georgia"]Perhaps I can add to this?

I have downloaded a driver posted on the website of the wifi card maker. It is for a Realtek 8185 chipset.

It has instructions to put it in - as I was told as advice on my first posting.

I can see that. But **I don't understand** those instructions. It does not tell me **enough**.

It tells me to run an included file which then runs many of the necessary instructions for you, which is helpful of course - as far as it goes.

BUT what do I do with the driver initially and those instruction files - where do I put it all before I run the first of the files. On a floppy disc perhaps? Or must it go in a specific folder? But what do I do with that? Do I have to tell the computer something if I do? And so forth. Do I have to go to that folder too, before running the instruction?

Here is what the the driver read me file says: [/FONT][/SIZE][/COLOR]

[SIZE="1"][COLOR="Sienna"]< Component >
The driver is composed of several parts:
    (1)source code
	r818x.tar.gz
	stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
	wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
	wpa_supplicant-0.3.8.tar.gz
    	
    (6)Example of supplicant configuration file
	wpa1.conf




< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

	(1)Build up the driver from the source code
         	./makedrv[/COLOR][/SIZE]

[COLOR="SeaGreen"][FONT="Georgia"][SIZE="3"]I don't understand this - where do I need to be when I type in this ? Where does the downloaded driver (and the other files) need to be?[/SIZE][/FONT][/COLOR]


    	[COLOR="Sienna"](2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )
	(3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.
[/COLOR]

[COLOR="DarkOliveGreen"][FONT="Georgia"][SIZE="3"]I have a big book about UBUNTU and have looked at lots of forums - but these basic things are usually left out.  Please be patient with people who have no knowledge - the answers may be simple but unless you can find them there is not any way to move forwards.

And without wishing to upset people - the advantage of Windows is that it mainly does not demand knowledge for these basic steps. 

Anyway I hope the question is sensible enough and you excuse my frustration - having got this far I hate being held up by tiny unknowns.

And I hope it will make the card work: most of the stuff I read about Linux is focused around upgrading and obtaining stuff on websites so without a connection...[/SIZE][/FONT][/COLOR]

---

### Post by jon_herr on 2007-03-21
I'm having the same problem - even though I compiled with correct headers without error my insmod 8185 comes back with Unknown symbol in module....

Anything new about this problem?

---

