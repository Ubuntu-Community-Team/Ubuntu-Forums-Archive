---
title: "wired network issues"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by boots_n_braces on 2009-02-06
Evening all, Im brand new to linux but getting there slowly! Im having issues with my wired internet connection. It works fine through windows but refuses to connect through ubuntu. It automatically lists it as " auto eth0 " so it finding it but if i try and connect it tries for a while then gives up.

Any attempt to view the internet or to ping a site just comes back with address can not be found. I followed the help section and tried pinging the ubuntu ip and it didnt say it couldnt be found it just sat there with 0% parcels doing nothing so i assume they were getting out but not coming back in?

Tried running it through the terminal with " sudo ifdown eth0" and it came back with interface "eth0 not configured" 

Any help would be brilliant!!

---

### Post by GepettoBR on 2009-02-06
> **boots_n_braces said:**
> Evening all, Im brand new to linux but getting there slowly! Im having issues with my wired internet connection. It works fine through windows but refuses to connect through ubuntu. It automatically lists it as " auto eth0 " so it finding it but if i try and connect it tries for a while then gives up.

Any attempt to view the internet or to ping a site just comes back with address can not be found. I followed the help section and tried pinging the ubuntu ip and it didnt say it couldnt be found it just sat there with 0% parcels doing nothing so i assume they were getting out but not coming back in?

Tried running it through the terminal with " sudo ifdown eth0" and it came back with interface "eth0 not configured" 

Any help would be brilliant!!


Can you please post the output of runing "sudo ifconfig" in a terminal?

---

### Post by tomsimmons on 2009-02-06
I don't suppose you have just done the upgrades that Ubuntu found?

I have, it pulled them all down, installed them all, restarted and now I haven't got a network connection.

This isn't like some other posts I've found where it looks broken but does work, the network connection is defective.  If you click the network icon, you can click the radio next to auto eth0, it scans and fails.  If you click and edit connections auto eth0 says 'never' at the end fo the line.  If you go to System>Administartion>Networking Tools eth0 is there.

ifconfig gives:

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:5d:17:8a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1224736695 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

I'll come clean, I had performed all the updates a couple of days ago on a fresh install, and this happened, I thought I might have done something silly.  There was one difference that time however, under Networking Tools only the loop back existed.

I have just installed afresh after that, accepted the updates when it offered after the first boot and here we are again.


Tom

---

### Post by boots_n_braces on 2009-02-06
sounds very similer to what ive got my connection says never next to the connection name etc. Havent installed any updates though just downloaded the latest version to day and installed for the first time. Is there anyway i can copy and paste between operating systems? so i dont have to type these lines out by hand lol

eth0 Link encap:Ethernet HWaddr 00:1d:92:b6:bd:6c
UP BROADCAST RUNNING MULTICAST MTU:64 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:5655 (5.6 kB) TX bytes:3193 (3.1 kB)
Interrupt:222 Base address:0x0000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:246 errors:0 dropped:0 overruns:0 frame:0
TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:15408 (15.4 kB) TX bytes:15408 (15.4 kB)

Hope that makes some sense! 
thanks for the help

---

### Post by tomsimmons on 2009-02-06
> **boots_n_braces said:**
> Is there anyway i can copy and paste between operating systems? so i dont have to type these lines out by hand lol

Mine are two separate machines, so I just shoved a USB pen in, created a text file and pasted into that :D

I guess by downloading to day you have the same as the CD I downloaded a few weeks ago plus the updates I've just downloaded.

If it's any help to anyone I have attached the Synaptic History of the updates.

Tom

---

### Post by boots_n_braces on 2009-02-06
what do you suggest then deleting this version and installing an older one?

cheers harry

---

### Post by tomsimmons on 2009-02-06
I've no idea I'm new to this game too.

I saw your post, thought that sounded the same, which I think we've confirmed.  Because I'm using an slightly older starting point I need to apply the updates to get the problem.

Hopefully with out ifconfig output the list of updates I apply to get the problem some genius will read this and give us a pointer on how to sort it out.

The folk on here are very, very good for this, unlike my previous attempts over the years you don't get shot at on here.


Tom

---

### Post by Zill on 2009-02-06
boots_n_braces:  Please open a terminal and post the output of the following code:
```
cat /etc/network/interfaces
```

---

### Post by boots_n_braces on 2009-02-06
Hi zill, i get 

auto lo 
iface lo inet loopback

hope that means something to you lol:D

---

### Post by Zill on 2009-02-06
boots_n_braces:  As there is no mention of eth0 there it looks like you will need to configure your network settings...

Menu System, Administration, Networking
On the Connections tab you should see the Ethernet connection and a designator such as "eth0" or "eth1" etc.

Click on the properties button to set the interface properties.

"Configuration" should be DHCP if you want to get the PC IP address automatically from your router.  Alternatively, use a Static IP address if you want to assign this manually.  In this case you will have to enter your required PC IP address, Subnet mask and Gateway address.

Make sure that "Enable this connection" is checked 

On the General tab you should see your PC name as the Hostname.

On the DNS tab you should see the IP address of your router in the DNS Servers list.  If this is not there then add it using the buttons.

If you have now made any changes, click on the "Deactivate" button then, a short while later, click on the "Activate" button to restart the interface.

Ensure that the Default gateway device shows your active interface (eth0 or eth1 etc.)  Click on OK to save and close the Network settings manager.

Hopefully, you will now have internet access and if you repeat the code I gave earlier you should now see a reference to the ethernet interface.

---

### Post by tomsimmons on 2009-02-07
Zill

I believe that boots_n_braces and I are suffering the same problem, only difference being that because he has only just downloaed 8.10 he has the problem from the start, where as I downloaded it several weeks back, so I start out fine, but then lose networking once I install the currently available updates.  It would seem there fore that something in the updates,now in the latest version of 8.10 is the problem.

Anyhow, my output to your last command was identical, so I was also waiting for your next post :)

> **Zill said:**
> Menu System, Administration, Networking
On the Connections tab you should see the Ethernet connection and a designator such as "eth0" or "eth1" etc.

Click on the properties button to set the interface properties..

Under Administartion I see Networking Tools, when I choose this I see the screen in the Network Tools attachment, this doesn't seem to correspond to your instructions, with instructions.

The only place I see anything like this is if I right click the network icon on the top panel and choose Edit Connections I get the screen in Network Connections attachement, and by editing Auto eth0 I get the screen in Editing Auto eth0, which as you can see is already on DHCP.

> Make sure that "Enable this connection" is checked.

On the Network Connection attachment you can see it says Never next to the Auto eth0, I'm guessing, but that sounds wrong?

As I say, networking was working fine until I installed the updates offered after rebooting from installation, they came via the internet.  Those updates (attached to a previous post in this thread) did contain some entries for networking, but which is responsible I don't know.


Tom


PS
Sorry to hi-jack your thread boots_n_braces

---

### Post by Zill on 2009-02-07
tomsimmons:  My apologies if some of the instructions I provided were inconsistent with your system.  I run 6.06 on my primary system, with 8.04 for "experimentation". The networking screens are similar on both 6.06 and 8.04 but have apparently been "improved" for 8.10 ;-)

Googling around it seems that there have been various bugs with 8.10 networking, which are steadily being resolved.  However, it is possible that a remaining bug *may* be causing your problem.  Hopefully, some other users of 8.10 will be able to help clarify this.

If a bug is to blame then the workaround is usually to configure files with the CLI, rather than the Networking GUI.  This means that you have to type various parameters into the files directly.  This is not a difficult task but isn't quite the usual "point and click".  Other users of 8.10 (Intrepid) should be able to help out here and clarify exactly what you will need to do.

In the meantime, I suggest you take a look at the "Edit Connections" tool you demonstrated in attachment #3.  I see that there is a button called "Routes".  Can you change anything with this?  Also, there is a tab called "Wired" - this *may* show the parameters I discussed earlier.

I suggest you make a note of all the current settings.  Then experiment with the various options available.  The default dhcp settings *should* work, but they may require a final tweak somewhere.  It is also worth trying to set a "static" IP address and see if you can connect with this.  Good luck.

---

### Post by boots_n_braces on 2009-02-07
cheers for the help zill im going to sit down and have a play in a minute 
Does this mean anything to you? sounds like this guys got a temporary fix but im not sure what i need to put were

[https://lists.ubuntu.com/archives/ubuntu-in/2008-October/004075.html](https://lists.ubuntu.com/archives/ubuntu-in/2008-October/004075.html)

---

### Post by tomsimmons on 2009-02-07
Zill

I guessed that you were probably using an older version, hence I clarified what I see with the pics.

The wired tab doesn't contain much, the MAC and a option to control MTU.

Could you post an example of what the network files should contain?

Thanks for all you help by the way

Tom

---

### Post by tomsimmons on 2009-02-07
Seeing as you don't appear to be able to remove updates, although I do have the history, I'm thinking I'll reinstall with the 8.10 CD I downloaded a few weeks back, then use RemasterSys to make a safe point.

I'll then work through the updates little by little and see if I can figure which one is mucking it up.  Hopefully this way I'll be able to post back to the community which of the latest updates prevents Networking.

Should only take me about 300 CD's and a couple of years :D


Tom

---

### Post by Zill on 2009-02-07
boots_n_braces/tomsimmons:  Let's open the terminal (Applications, Accessories, Terminal) and try editing the /etc/network/interfaces file...

First copy the original file as a backup!
```
sudo cp /etc/network/interfaces /etc/network/interfaces_backup
```
Then use the editor "nano" to edit the file:
```
sudo nano /etc/network/interfaces
```
The file should already contain the lines
auto lo
iface lo inet loopback

Type the following new line (use eth(number 0) **not** eth(letter O))
auto eth0

If there are any other lines then add a "#" sign at the start of the line.  This is the standard way of "commenting out" a line so that it is ignored.

The resulting file should only show three "active" lines.

Hit Ctrl-O to save the file and Ctrl-X to exit.

Reboot

The PC should now connect to the internet using DHCP.  Keep your fingers crossed. :-)

---

### Post by boots_n_braces on 2009-02-21
Hi all sorry for the lack of replies on this been a crazy week! Ok ive tried the suggested soloution to no avail and a couple of others i found a different site but still nothing. 
I downloaded damn small linux and im currently running it off a disc to see if that worked but it has the same issues no errors but just wont connect?!?!

Im baffled is there anything vista could be buggering around with thats causing the issues?

thanks,
harry

---

### Post by boots_n_braces on 2009-02-21
p.s ive tried connecting on damn small linux with and without dchp and neither seems to make a difference

---

### Post by jimrz on 2009-02-21
sorry mis-read it

---

### Post by abyssius on 2009-02-21
> **boots_n_braces said:**
> p.s ive tried connecting on damn small linux with and without dchp and neither seems to make a difference

boots_n_braces

If you want to try editing your /etc/network/interfaces file as suggested in the earlier posts. 

It should end up looking something like this:
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
gateway xxx.xxx.xxx.xxx

auto eth0

```

Replace the xxx.xxx.xxx.xxx portion of the gateway line with the actual IP address of your router.

After you do this, issue:
```
sudo /etc/init.d/networking restart
```

maybe this will get you connected.

---

### Post by abyssius on 2009-02-21
> **jimrz said:**
> looking at your screenshots it appears that you are in the"Wired" tab and need to select the"wireless" tab in order to work on your wifi connection.

give that a try and see what you can come up with

The name of the thread is 'wired network issues'. I'd assume from this that his problem isn't a wifi issue.

---

### Post by Zill on 2009-02-22
boots_n_braces:  Please advise the IP address of your router (eg 192.168.0.x) and post the outputs from the following commands...
```
cat /etc/network/interfaces
```
```
ifconfig
```

---

