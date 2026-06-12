---
title: "Where is the &quot;Connect&quot; button?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by kilburncat on 2010-11-06
I've downloaded Ubuntu 10.10 onto a disc and am trying it out from the disc. I've set up various combinations in what I understand is the Network Manager in order to make a wireless conection, but I'm not sure I'm doing the right thing because nowhere do I see a 'Connect' button either highlighted  or dimmed, and it does not connect automatically although I have checked this box. I am using a USB plug in device but it works OK with Win XP so I don't think it's that.:(

---

### Post by Hippytaff on 2010-11-06
so you can't connect via usb wireless device using the live cd? :-)

just making sure I understand :-)

open a terminal (CTRL ALT+T)
type
```

lsusb

```and post the out put here :-)

if you decide to install ubuntu, you might need to do a few things to use your usb wireless device, though ethernet will work fine :-)
and welcome :-)

---

### Post by anewguy on 2010-11-06
And, when you get the driver installed for Linux and get the wireless adapter working, there still won't be a single "Connect" button.  You will either have an auto-logon network that it will connect to (a default network) or you will have to select the network to connect to.

Dave ;)

---

### Post by kilburncat on 2010-11-07
Yes I am using Ubuntu from a CD.
I had been using the **Configure VPN** in the top r/h corner, I opened the **Wireless** tabs, entered what I believe are the details required, clicked **Apply** and nothing happened.
I opened the box as described by depressing **Ctl. Alt, T**, a box with some text already in it opened, I typed **1susb** after that text and pressed **Enter **key or **Return** key and the response **Command not found** appeared.
I'm obviously not doing it correctly, I am an absolute Ubuntu beginner.

---

### Post by ironic.demise on 2010-11-07
> **kilburncat said:**
> Yes I am using Ubuntu from a CD.
I had been using the **Configure VPN** in the top r/h corner, I opened the **Wireless** tabs, entered what I believe are the details required, clicked **Apply** and nothing happened.
I opened the box as described by depressing **Ctl. Alt, T**, a box with some text already in it opened, I typed **1susb** after that text and pressed **Enter **key or **Return** key and the response **Command not found** appeared.
I'm obviously not doing it correctly, I am an absolute Ubuntu beginner.

ctrl+alt+t should open terminal
terminal starts with username@pcname:
then type "lsusb" (not 1susb, it's a lower case L)
give the output please, thankyou
Hope to help

---

### Post by alphacrucis2 on 2010-11-07
> **kilburncat said:**
> Yes I am using Ubuntu from a CD.
I had been using the **Configure VPN** in the top r/h corner, I opened the **Wireless** tabs, entered what I believe are the details required, clicked **Apply** and nothing happened.
I opened the box as described by depressing **Ctl. Alt, T**, a box with some text already in it opened, I typed **1susb** after that text and pressed **Enter **key or **Return** key and the response **Command not found** appeared.
I'm obviously not doing it correctly, I am an absolute Ubuntu beginner.

Configure VPN is the wrong choice unless you really did want to use a **V**irtual **P**rivate **N**etwork. In the first instance, follow the instructions given by ironic.demise so we can see what's what.

---

### Post by ironic.demise on 2010-11-08
Wired or wireless networks should appear above *configure VPN >*
You should be able to click one and it instantly connect or ask for an encryption password.
(This is assuming you are using the default 10.10 network manager)

---

### Post by kilburncat on 2010-11-08
I opened the box with **ctl alt t** and entered **lsubs** and it gave a list of 4 items including my belkin wireless usb connector, but I was not sure what to do next. I closed the window and no connection was made so I am missing something out. 
The **Help** mentions a connection wizard and I thought the VPN set-up was this wizard but I got nowhere with it.

---

### Post by kilburncat on 2010-11-10
I'm having trouble making a wireless connection. I've been advised to open a terminal so
I opened the box with **ctl alt t** and entered **lsubs** and it  gave a list of 4 items including my belkin wireless usb connector, but I  was not sure what to do next. I closed the window and no connection was  made so I am missing something out. 
The **Help** mentions a connection wizard and I thought the VPN set-up was this wizard but I got nowhere with it. Is there not an easier way to do it?
I am using Ubuntu 10.10 directly from the disc in the drive (I haven't installed it yet) and my wireless connection comes via a USB plug in device, which works OK with Windows XP.

---

### Post by amjjawad on 2010-11-10
> **kilburncat said:**
> I'm having trouble making a wireless connection. I've been advised to open a terminal so
I opened the box with **ctl alt t** and entered **lsubs** and it  gave a list of 4 items including my belkin wireless usb connector, but I  was not sure what to do next. I closed the window and no connection was  made so I am missing something out. 
The **Help** mentions a connection wizard and I thought the VPN set-up was this wizard but I got nowhere with it. Is there not an easier way to do it?
I am using Ubuntu 10.10 directly from the disc in the drive (I haven't installed it yet) and my wireless connection comes via a USB plug in device, which works OK with Windows XP.

System > Preferences > Network Connections

---

### Post by toekneewood on 2010-11-10
Take a look in the top right corner of your screen.  You should see an icon that will list all available wireless networks.  Click the one you need.  That application is called "network manager"

---

### Post by ironic.demise on 2010-11-10
lsusb should give an output, post that output here so we can read it and see if we see anything wrong.
 
Right click the Network icon in the panel (The on that provided you with the VPN menu) and click "edit connections"
That's the wizard you want.
 
If that fails check to see if your driver is supported under NDISwrapper

---

### Post by kilburncat on 2010-11-10
I'm not having much luck. I can't find an available networks icon in the top right hand corner. In System>Preferences I can find Network Connections, and I've tried editing wireless connections putting different data in various boxes and then clicking 'Apply' but nothing happens.:confused:

---

### Post by irv on 2010-11-10
Let's start from the beginning. If you can't see the Network icon at the top right of your screen, you might not have a driver loaded. 
First, you will need to plug in a Network cable to get on the Internet. Next go to System> Administration> Additional Drivers. It will search for your hardware and list the driver(s) to select from. Pick the right driver. After it installs you should be able to disconnect the cable and it should find your wifi.
If this works you will be safe to install Ubuntu, but remember when you have to do this again once Ubuntu is installed.

---

### Post by kilburncat on 2010-11-10
Many thanks, Irv, I will do that. 
Another puzzling thing is that when I left the pc for a while the screen went blank, and it is now asking me for a username and password for Ubuntu, even though I have not entered this data, I am merely trialling it from the disc.:(

---

### Post by irv on 2010-11-10
> **kilburncat said:**
> Many thanks, Irv, I will do that. 
Another puzzling thing is that when I left the pc for a while the screen went blank, and it is now asking me for a username and password for Ubuntu, even though I have not entered this data, I am merely trialling it from the disc.:(

It was you screen-saver that kicked in. I would think if you just hit enter for the user name and password it would just come up again. That is something that should have been looked at when running from the live CD.

---

### Post by corncob on 2010-11-10
> **kilburncat said:**
> Many thanks, Irv, I will do that. 
Another puzzling thing is that when I left the pc for a while the screen went blank, and it is now asking me for a username and password for Ubuntu, even though I have not entered this data, I am merely trialling it from the disc.:(

For a username I kinda remember seeing "ubuntu" on the upper right of the screen when using a live CD.  I don't know about the password but I'd try "ubuntu" there too.

---

### Post by anewguy on 2010-11-10
First, hang in there.  Second, when we ask you to do things like the lsusb, don't expect that this is going to magically get your wireless working.  We are usually asking for information first to help us with diagnosing your true problem and then coming up with a solution.  When we get to the solution part, I can guarantee we'll ask you to reply back letting us know if you see any networks then.  Up until then, we're hunting for information.

Dave ;)

---

### Post by Elfy on 2010-11-10
Please do not post duplicate threads -

It will lead to confusion.

Merged this time.

---

### Post by kilburncat on 2010-11-20
After a great deal of moving of furniture and the router :twisted:, I plugged the (6 year old) desktop pc into the router via an ethernet cable, it initially recognized the connection but rapidly said that the Avahi (software?) was not compatible and that it would disconnect, which it did.

---

### Post by Hippytaff on 2010-11-20
so...are you sorted? :-)

let us know :-)

---

### Post by kilburncat on 2010-11-21
No I'm not sorted at all I'm afraid. I thought I would take the plunge and install it alongside Windows but it recommended being connected to the net, hence the ethernet cable. As I could not connect, I abandoned installation, but I cannot connect when I am using Ubuntu from the disc that it is on. As mentioned earlier, I've opened the terminal and entered lsusb and it seems to identify my Belkin wireless connection, although I am not sure what to do with these terminal boxes. And not sure what I could do now.

---

### Post by Hippytaff on 2010-11-21
You might need to install the third party drivers for the wireless after you install it but ethernet should work without a problem :-s

---

