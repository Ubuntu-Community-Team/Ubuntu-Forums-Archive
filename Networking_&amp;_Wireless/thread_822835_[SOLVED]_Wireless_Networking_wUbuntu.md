---
title: "[SOLVED] Wireless Networking w/Ubuntu"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by CoCoKnots on 2008-06-08
I have never tried to connect a networking system with any O/S. We now have two computer using Ubuntu & about to convert a third. We are using a 'Linksys' wireless system. How do I get these things to communicate ?

---

### Post by issih on 2008-06-08
I'm afraid we are going to need quite a lot more information than that :s

You say you are using a linksys system....by that do you mean you have a linksys wireless router?

---

### Post by CoCoKnots on 2008-06-08
Yes, It's a Wireless -G 2.4 Broadband router. I am using a Sony VAIO VGN-FE780G Notebook & a Dell 1525... Is this the type of thing whic will require a lot ok special knowledge ?

---

### Post by CoCoKnots on 2008-06-08
Are there basic instruction where I might find this procedure ?

---

### Post by issih on 2008-06-08
It all depends how lucky you are, and what exactly you are trying to achieve.

Ubuntu does come with drivers built in which can work with a lit of wireless hardware, unfortunately there are still a LOT of wireless cards that do not work out of the box, and if you are in that situation then you will have to do a fair amount of fiddling to get each computer to see the router.

The only way to find out how lucky you have been in the wireless hardware lottery is to try and connect each pc in turn to the router.

!) Log into the router via the web interface, check that the wireless lan is set up to use dhcp, find out what the ssid (network name) is, and ensure that the router is broadcasting the ssid, finally turn off all encyption.

N.B. turning off encryption is being done so that in the testing phase things are as simple and vanilla as possible, you must switch encryption (really wpa or better) on after you have confimed if things are working.

Now pick a computer, any computer...

I will now describe how this will go if you are lucky.

Go to the network manager applet (the icon in the notification area up in the top right). Right click on the icon, the drop down menu should have an "enable wireless" check box in it, ensure that is checked. Now left click on the same icon, and the drop down menu should present a list of ssids belonging to networks detected in the vicinity. Simply click on the one that is your network's ssid, and with luck you should end up connected to the router, and therefore the internet.

If there is no "enable wireless" checkbox, or if the list of networks is empty (check it s few times), then it is probable that that the wireless hardware in that computer needs a driver module, in order to work out what you will need to do to enable the hardware in a non functioning pc, we will need to know the exact hardware it uses, as a first step open a terminal window and enter:

```
sudo lshw -C network
``` 

and post the resulting output here.

Do this for each pc you want to connect to the network.

Once you have got to that stage, you can start thinking about what protocols you want to use to talk from one pc to another on your own little local wireless network, there a few options, but you need to get all the above sorted first.

Sorry its not just point click work, sadly this is just the way it is

---

### Post by CoCoKnots on 2008-06-09
OK... I entered the sudo command onto a terminal page & this is what it looks like. I have done this on both notebooks using Ubuntu. We are both accessing the internet fine on the Linksys wireless G router. What should I do next to get these things to communicate ?

---

### Post by issih on 2008-06-09
Excellent, if you can see the internet with both pc's then you are 90% of the way there.

Install the package nautilus-share on each pc, to do this open a terminal and type:

```
sudo apt-get install nautilus-share
```

Then enter your password when prompted.

Once the install completes reboot the pc.

Now open a file browser (e.g. Places->Home Folder) and navigate to the folder you want to share. Right click on the file and select "Sharing Options".

The resulting dialog box has three check boxes.

The first merely turns sharing on or off for the selected folder.

The second defines whether network users will be able to alter the contents of the folder, or merely have read access to it.

The final one is a bit more complicated, if it is left unchecked, then only people with a user account on the pc sharing the folder will be able to access it over the network (and will have to enter their username and password to prove it), if guest access is enabled, people can access the folder without knowing any usernames or passwords.

Once a pc is sharing a folder, then to access it from the another computer go to:

Places->Network

The resulting browser will hopefully be self explanatory (N.B it will show both local and remote nodes on the network)

Hope that makes sense and lets you get what you want running.

---

### Post by CoCoKnots on 2008-06-10
Everything looks like it is trying to work. When I get to the part where I right click on the file & toggle the access lines, It comes back with an error 255 netusers disabled... This shows up on both computers. Is there something missing in the download ?

---

### Post by issih on 2008-06-10
Hmmmn, lets just establish something, what version of ubuntu are you running on these computers? I ask as it looks like the tools used for sharing folders changed, I've told you what to do for a hardy heron 8.04 installation, if you are running something else, you may need a different package.

Oh and did you reboot after installing nautilus share?, there are lots of reports saying that is essential to get things working.

---

### Post by CoCoKnots on 2008-06-11
Yes, I have re-booted a couple of times. I remember reading something to that effect. However, I am using 7.10 and not the newer 8.04.

---

### Post by issih on 2008-06-12
Aha, that explains things somewhat, as you are using gutsy rather than hardy we need to do this slightly differently.

First of all undo what we did last time :s

```
sudo apt-get remove nautilus-share
```

Then go to System->Administration, and find the menu item relating to file sharing (I forget its exact name, but its there somewhere). I believe if you open that it should automatically install the packages you need to get file sharing working in gutsy.

Once that is done you should be able to configure shared folders either through that same gui, or through a right click in nautilus.

Thats all from memory/a bit of googling, as I can't poke around on a gutsy install myself anymore, all my boxes are on hardy now.

---

### Post by CoCoKnots on 2008-06-12
Thanks again issih... Great Job

---

