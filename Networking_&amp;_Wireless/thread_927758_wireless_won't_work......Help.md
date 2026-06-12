---
title: "wireless won't work......Help"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by ryan518w on 2008-09-23
I just installed ubuntu 8.10 (i think thats what version is, what ever the new one is) and the wireless won't work. when i plug it up directly to my router it works fine but not wireless. with out the cord, and i click on the network icon on the top of the screen it says "no network connections". I also have sabayon linux and vista on here and it works fine with those two but not ubuntu.......Please help....It is a gateway mt3707 laptop with 1gb ram and dual core cpu, ati radeon graphics

---

### Post by Idefix82 on 2008-09-23
You didn't post the most important info though, the make of the WiFi card :)

---

### Post by pedro_orange on 2008-09-23
If you don't know your NIC hardware make/model open a terminal and type the following:

```
sudo lshw | less
```

Press space bar until you see a heading along the lines of -network:0 or -network:1
This should tell us what you need to know.

You should also note it's logical name. (eth0, eth1, ethX)

You can use tools like ethtool and iwlist to help troubleshoot further.

---

### Post by issih on 2008-09-23
Actually a slightly better command would be:

sudo lshw -C network

as that will just list the networking hardware, rather than everything...

Note that these commands should be run in a terminal window, and you can copy and paste from that terminal window either with a mouse, or using ctrl+shift and c/v.

Also be aware that any time you run a command using sudo (super user do) you are granting temporary access to the guts of your system to the following command/s. You are therefore prompted for a password (which is just your login password, type it and hit enter)

sudo is powerful, and should really only be used if you understand what the commands are doing...just a warning, nothing to worry about here :)

---

### Post by ryan518w on 2008-09-23
*-network UNCLAIMED
                description: Ethernet controller
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 9
                bus info: pci@0000:08:09.0
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=64 mingnt=32

This is the only network related thing i got I hope this helps

---

### Post by pedro_orange on 2008-09-23
Did a quick google, and most people have had success with the ndiswrapper, please see the following link: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by ryan518w on 2008-09-23
This form did not work because one of the links were dead......any other ideas

---

### Post by issih on 2008-09-23
Searching around a bit I found this:

[http://jimvernon.com/archives/53](http://jimvernon.com/archives/53)

Basically you need to use ndiswrapper to allow you to use information gleaned from the windows drivers.

The blog post I've linked should help, but personally I'd just install the package ndis-gtk which gives you a little gui to control ndiswrapper.

All you need do then is grab the driver referred to in that link, and unzip it to get at the .inf file, the rest is done in nice friendly guis.

Hope that helps

---

### Post by ryan518w on 2008-09-23
This form did not work because one of the links were dead......any other ideas

---

### Post by shanix on 2008-09-23
Please run the:

lspci -vvnn | grep Wireless

If nothing shows up, please copy and paste the result from:

lspci -vvnn

to pastebin.com

Thanks

---

### Post by ryan518w on 2008-09-23
It still did'nt work I think i need help with this form

---

### Post by shanix on 2008-09-23
without you provide the necessary information, it is hard for us to help you...

---

### Post by issih on 2008-09-23
What do you mean form? I don't follow at all. Did you install ndiswrapper, did you download the windows drivers and extract an inf file. did you load the inf file into ndiswrapper.

Tell us what you have done, jsut saying this form doesn't work tells us nothing useful, it doesn't even really make sense I'm afraid

---

### Post by ryan518w on 2008-09-23
This form did not work because one of the links were dead......any other ideas

---

### Post by ryan518w on 2008-09-23
when i tried to do it worked until it said cammand not found on the last like two cammands i typed from the instructions. I just need another idea

---

### Post by pedro_orange on 2008-09-24
You do not need another idea, you should try and actually install the ndiswrapper.

Tell us where you went wrong, then perhaps we can help you further.

1 - Did you manage to add the correct repo?
2 - Did you disable the original driver?
3 - Did you download a Windows driver for your particular network card?
4 - Did you install the driver?
5 - Could you load the driver?

If you tell us what you did and did not do, we can suggest what to do. Tell us what command did "not work".

---

### Post by ryan518w on 2008-09-24
it says "Once you have ndiswrapper installed, unzip the file you downloaded and change your terminal to that directory.  Then install the drivers with these commands:



    sudo ndiswrapper -i net8185.inf



    sudo ndiswrapper -m



    sudo ndiswrapper -mi



    sudo ndiswrapper -ma



    sudo modprobe ndiswrapper
"
I don't know how to change my terminal to a directory

---

### Post by issih on 2008-09-24
To change directory in a terminal you use the cd command:

```
cd ..
```

takes you up one level

```
cd directoryName
```

takes you into the directory directoryName one level below where you currently are.

alternatively you can specify the whole path from the root of the filesystem "/" e.g.:

```
cd /home/dre/desktop
```

If you this uncomfortable with the terminal you would be better off installing ndisgtk and doing things via the gui.

run this command in a terminal:
```
sudo apt-get install ndisgtk
```

and enter your login password when prompted.

Now in the main menu go to System->Administration->Windows Wireless Drivers.

In that gui hit add or install or whatever the button is called and then use the file browser to select the 8185.inf file from the unzipped driver.

Hope that helps

---

### Post by ssanjay on 2008-09-24
I just installed Ubuntu 8.0.4 on my laptop. and I can't get wireless to work on my AR242x card, any suggestions?

---

### Post by ryan518w on 2008-09-26
Thinx for all u alls help i gave up and went back to 7.10 and it works but thanx though

---

