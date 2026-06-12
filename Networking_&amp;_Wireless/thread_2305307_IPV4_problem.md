---
title: "IPV4 problem"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by jules6 on 2015-12-04
Hi Guys,
  I am setting up my Ubuntu server. 
  Can anyone help me find the IP address. When I  enter "ifconfig"
   No IPV4 address comes up, I have tried everything I can think of. All other devices on my network 
are working OK.

Thanks in advance.

Regards,
Jules.

---

### Post by newbie-user on 2015-12-04
What exactly do you see when you type ifconfig? You should see the lo interface as well as another interface, such as eth0.

---

### Post by jules6 on 2015-12-05
Thanks for reply.
I see all eth0 but does not show any IP address as it does here (networks2 attached)
The section I marked out in orange does not show.

Thanks.

---

### Post by steeldriver on 2015-12-05
It would be better to tell us what **is **there than what **isn't**

Is there an IPv6 address? What are the contents of your /etc/network/interfaces file?

---

### Post by jules6 on 2015-12-05
Sorry I will get on it again over weekend. I have been unable to look again until now.
I will put in the command you suggest and report back.

Thanks.

I have a pic of screen (attached)
I have tried to input  /etc/network/interfaces file but won't allow me access.
Is there another command I could try please?

---

### Post by steeldriver on 2015-12-05
You need to 'cat' or otherwise print the file contents

```

cat /etc/network/interfaces

```

Based on the screenshot, it looks like your device has obtained an IPv6 address - if that's not what you want, there are ways to disable IPv6 I think

---

### Post by jules6 on 2015-12-05
Do I enter the word "cat" first?
Sorry I am a novice at ubuntu

I have done that.
I get:
"The primary network interface allow hotplug eth0 interface eth0 inet dhcp"

Hope someone can help me through commands to change ip.
Thanks in advance.
Regards,
Jules.

---

### Post by steeldriver on 2015-12-05
Is that the exact, complete contents of the /etc/network/interfaces file? it should at least have an entry for the loopback interface (lo), something like

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

---

### Post by jules6 on 2015-12-06
Thanks steeldriver, the code you have shown is exactly what I get.

---

### Post by newbie-user on 2015-12-07
You can manually set the interface to have a static ip address by editing the /etc/network/interfaces file to look something like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        gateway 192.168.1.1
        broadcast 192.168.1.255
```

Additionally, you could check your DHCP server to see if it's purposefully not giving an ip address to your machine--things like DHCP reservations, small scope size, etc. Could be a bad network cable too.

---

### Post by jules6 on 2015-12-07
Thanks, Do I enter the same as what you show in code area, but select my chosen address?
What is the broadcast address for please?
I know the gateway is my router address but what is network addres please?

---

### Post by newbie-user on 2015-12-07
You can get all the network information from the other computers on your network. From the screenshots you posted a while ago, your network information is as follows:

network address: 192.168.2.0
broadcast address: 192.168.2.255
netmask: 255.255.255.0

The network address is like your home address, it's where the computers on your network live. The individual ip address is like the specific room of the house. The broadcast address is like the ability to shout in the house and have everyone hear you.

Is you router doing DHCP for the network? Have you already checked the DHCP settings?

---

### Post by jules6 on 2015-12-07
Thanks I will try what you said

The problem I have is because I can't find IPV4 address I can't communicate with it from anywhere. I need to set an IPV4 address instead of IPV6

---

### Post by newbie-user on 2015-12-08
Ok, so then try setting a static ip in /etc/network/interfaces. Just make sure you use an ip address that hasn't already been handed out to another device on the network. Edit /etc/network/interfaces to look something like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        gateway 192.168.1.1
        broadcast 192.168.1.255
```

---

### Post by Hadaka on 2015-12-08
Hi, your screen shots in post #3 and #5 appear to be wired ethernet connections
not wireless. You will notice in post #3 you also have an ipv6 address, this is normal.
Screen shot,post #5 shows no DHCP IP address from the router. First let's compare some other things
between the two..working post #3 Not working post #5.
please post the output from the working and non working computers from these commands.
also you can COPY and paste to the thread here from the terminal instead of screen shots.
please COPY and paste the output of..
from both computers.
```
cat /etc/network/interfaces
cat /etc/resolv.conf
```
once we fix this, we will address the no IP from the router issue.
thanks.

---

### Post by jules6 on 2015-12-08
Thanks guys for helping me through this.
I will have a go this evening and report back

Hi Hadaka, thanks.
I input:   cat /etc/network/interfaces 
Then: cat /etc/resolv.conf
I get back: nameserver: 192.168.0.1
this is furthest I have got thanks.
What to do nest please?

---

### Post by Hadaka on 2015-12-08
Hi, what i want is for you to do as i requested, i don't want a written
it says this, or a screen shot...i want you to COPY and paste the output of
those commands.,like this..
```
hadaka:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback

```
i asked for you to do this with both computers...the working one 
and the one that is not working.
please try again.

---

### Post by jules6 on 2015-12-08
You mean my working linux box not my windows PC?

This is what I get from my other linux box

---

### Post by Hadaka on 2015-12-08
Hi, perhaps i was not clear in my request, so i will ask one more time,

please post the output from both computers.....C O P Y... and  P A S T E
the command...and the output...from the TERMINAL to this THREAD.

BOTH COMPUTERS...BOTH COMMANDS like this...

computer 1
```
[hadaka:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback
```
```
hadaka:~$ cat /etc/resolv.conf
# Generated by NetworkManager

nameserver 127.0.0.1
```

computer 2.
```
hadaka:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback
```
```
hadaka:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.0.1

```

---

### Post by steeldriver on 2015-12-08
@Hadaka the OP may be having difficulty pasting command output to this forum without network connectivity on the affected machine

I guess there's the good ol' sneakernet - jules6 do you have a USB stick you can use to copy stuff with?

---

### Post by Hadaka on 2015-12-08
That is a possibility, however reading the entire thread I came to the conclusion that..
```
root@Dragon
root@ringo - No DHCP address
root@bn750
 #You mean my working linux box not my windows PC? 

```
There is atleast 3 linux machines and also a windows machine, sorry to say i have no windows
knowledge and therefore will not be able to help further.
sorry i was unable to resolve your problem.

---

### Post by jules6 on 2015-12-09
Thanks , but we don't need to worry about windows do we?
I can't copy and paste from the system I am trying to set up because it is not connecting to my network yet.
That is what i am trying to do, give it an IPV4 address

Thanks steeldriver,
  but don't understand where to copy from. Will screen shot not do?

---

### Post by steeldriver on 2015-12-09
Screenshots will do fine for now. Or you can **carefully** type the outputs - we can try to keep them to a minimum to make that less onerous.

Can we take a step back and see exactly what hardware we're working with here please? Here's a command that should gather that information:

```

lspci -vnn | awk -vRS= -F'\n' '/\[02.0\]/ {print $1; print $NF}'

```

---

### Post by jules6 on 2015-12-09
Thanks for taking me through this, I appreciate it. I know I am not used to it, but we will get there.
Do I just put in that command and give you the info on screen?

---

### Post by steeldriver on 2015-12-09
Yes please

---

### Post by jules6 on 2015-12-09
Please give me a little time, will about an hour be OK to give you the info?

---

### Post by steeldriver on 2015-12-09
No problem - whenever

---

### Post by jules6 on 2015-12-09
Thanks.

Hi Steeldriver,
  Been a hell of a day, sorry. Just got round to putting your command in, this is what I got back:
03:00.0 Ethernet Controller [0200]: Realtek Semicondutorco.,Ltd. RTL8111/8168
B PCI  Express  Gigabit Ethernet Controller [10ec:8168] (rev 0c)
Kernel driver in use:  r8169

There is a colon between 10ec and 8168 but does not appear above.

Hope this helps.

---

### Post by steeldriver on 2015-12-09
OK this may be an issue of the wrong driver getting loaded - but I'm not up-to-date in this area. Let's see if one of the network driver gurus stops by, if not I will send out the bat signal.

In the meantime can you please execute the following 2 additional commands and post their outputs

```

uname -mr

tail -1 /etc/lsb-release

```

Thanks for your patience

---

### Post by jules6 on 2015-12-10
No problem, thanks for your help!!
I have put in the first command, I get back:
3.2.0-4-amd64 x86_64
Put in second command and I get back:
Cannot open /etc/lsb-release No such file.

Thanks.

Hi Steeldriver,
did that info help at all please?

---

### Post by chili555 on 2015-12-11
My colleagues have called in a specialist for a consultation; a third opinion, if you will.

First, please confirm the network numbers by consulting other devices on the same router as the computer in question. I have read above numbers like 192.168.1.xx, 192.168.0.xx and 192.168.2.xx. Obviously, if you declare the wrong street address, you will never connect. 

Assuming that you have confirmed, say 192.168.**2**.xx is correct, please do:```
sudo nano /etc/network/interfaces
```Populate the file like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.2.102
        netmask 255.255.255.0
        gateway 192.168.2.1
        dns-nameservers 8.8.8.8 192.168.2.1
```Proofread carefully, save (write out) and close the text editor. Get the system to re-read and use the changed file:```
sudo ifdown eth0 && sudo ifup -v eth0
```The -v for verbose will produce some output that you can read (and tell us about) in case there is an error or warning. Check:```
ifconfig
```Did you get the x.102 address? Can you reach the internet?```
ping -c3 192.168.2.1
ping -c3 www.ubuntu.com
```

---

### Post by jules6 on 2015-12-11
Thank you all very much for helping me.
I will get you all the info over the weekend if thats OK?

Cheers,
Jules.

---

### Post by chili555 on 2015-12-11
> **jules6 said:**
> Thank you all very much for helping me.
I will get you all the info over the weekend if thats OK?

Cheers,
Jules.Certainly! We look forward to your report.

---

### Post by jules6 on 2015-12-11
Thanks again

Hi  chili555,
I have tried  first command:
sudo nano /etc/network/interfaces

Says " command not found"

When I log in with my username and pass I just enter:
/etc/network/interfaces
an I get back: "permission denied"

When I enter: cat /etc/network/interfaces, it says:
" iface eth0 inet dhcp"

Hope this helps?

---

### Post by chili555 on 2015-12-12
We need some way to edit the file. In order to install nano, we need an internet connection. Nice little catch 22 we have here, isn't it?

Confirm that you have an eth0 interface:```
ifconfig
```We hope we see something like:> eth0
 Link encap:Ethernet  HWaddr xx:de:f1:3e:b2:xx
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
 If so, let's try to kick it to life:```
sudo ifup -v eth0
```The -v for verbose should produce some output giving us some clues as to what's going on behind the scenes.

If it appears to connect, that is, get an IP address from the router, test:```
ping -c3 www.ubuntu.com
```If you get ping returns, you are connected. Then do:```
sudo apt-get update
sudo apt-get install nano
```Then edit the file as above, including the *lo* stanza.

---

### Post by jules6 on 2015-12-13
I'll get on to it now.
Thanks.

Hi,
 I have entered "sudo ifup -v eth0"
Won't accept sudo command.
Tried without sudo and says interface already configured.
Then fried to ping ubuntu.com but says unknown host.

---

### Post by steeldriver on 2015-12-13
Hmm...

In an earlier post, you reported

> **jules6 said:**
> 
Cannot open /etc/lsb-release No such file.


and now you are telling us

> **jules6 said:**
> Hi,
 Won't accept sudo command.


Are you sure this is an Ubuntu system at all? Something is not adding up here. 

What does "won't accept" mean? 

Please post the **precise error message**: the difference may not seem important to you, but it does to us

---

### Post by chili555 on 2015-12-13
I suspect the absence of the loopback stanza in the file /etc/network/interfaces is a big problem. I don't know if you got bad advice or if you executed the command in error, but this is wrong:> When I enter: cat /etc/network/interfaces, it says:
" iface eth0 inet dhcp"
That suggests that you _overwrote_ the file; you needed to append the file. There is a big difference. However it happened, we need to fix it. Please try:```
echo "auto lo"  >  /etc/network/interfaces
echo "iface lo inet loopback"  >>  /etc/network/interfaces
```Please copy these carefully. The exact wording, punctuation, spacing, etc. is crucial. *Proofread carefully before you press Enter.*

If these commands are accepted without error or complaint, continue:```
echo "  "  >>  /etc/network/interfaces
echo "auto eth0"  >>  /etc/network/interfaces
echo "iface eth0 inet dhcp"  >>  /etc/network/interfaces
```I have my fingers crossed!

Let us know what happens and we'll proceed.

---

### Post by jules6 on 2015-12-13
OK chili555,
 I have entered all the code you told me and got no errors back, so far so good.
What do I do now please?

---

### Post by chili555 on 2015-12-13
Try to reboot and see if the ethernet connected:```
ifconfig
ping -c3 www.ubuntu.com
```And, more importantly, see if 'sudo' has returned:```
sudo apt-get update
```

---

### Post by jules6 on 2015-12-13
OK,
 I rebooted and noticed that it was giving me lines of trying to find DHCP server on port 67 
while booting.
Still not connecting to network though.

---

### Post by chili555 on 2015-12-13
Let's have a look at:```
sudo ifdown eth0 && sudo ifup -v eth0
```The -v for verbose should produce some clues. Does it try to get an IP address and fail? Or is there some other error? 

I realize that you can't copy and paste the output, so just give us the summary and include any details you think are crucial.

---

### Post by jules6 on 2015-12-13
Thanks, tried that command and it says "Sudo: command not found"

---

### Post by jules6 on 2015-12-13
Also just tried to ping  192.168.2.1
Comes back with network unreachable.

---

### Post by chili555 on 2015-12-14
What does this tell us?```
cat  /etc/resolv.conf
```

---

### Post by jules6 on 2015-12-15
Hi Chili555, sorry for late response.
Just having another go now, I have put in the code you said to and got back:
Nameserver 192.168.0.1   
Is this looking better?

---

### Post by chili555 on 2015-12-15
> **jules6 said:**
> Hi Chili555, sorry for late response.
Just having another go now, I have put in the code you said to and got back:
Nameserver 192.168.0.1   
Is this looking better?It's looking more horrible by the moment. Here is another case of overwriting instead of appending.

Mine reads:```
cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```These entries are important.

Frankly, so much has been obliterated that I am not sure there is any other way aside from a clean reinstall.

---

### Post by jules6 on 2015-12-15
Can you take me through a clean install please?

---

### Post by chili555 on 2015-12-15
You just boot from the DVD or USB you used to install originally and select 'Install Ubuntu.' It will ask if you want to install along side your current install or wipe it out and start new. You want the latter. After ten or so minutes, you should be all set and you and I alone will fix up the ethernet in just a few steps.

While it is running, please verify the network details on other devices on the same network; 'Pads, 'Pods, phones, windows computers, etc. We need the gateway address from a couple of them. 192.168.x.what?

---

### Post by jules6 on 2015-12-16
Thanks chili555, where can i download the software please?

---

### Post by jules6 on 2015-12-16
I have found software from here is this correct?
[http://www.ubuntu.com/download/server/thank-you?country=GB&version=15.10&architecture=amd64](http://www.ubuntu.com/download/server/thank-you?country=GB&version=15.10&architecture=amd64)

I am installing it on a Intel NUC DN2820FYKH pc. Will that be OK?

---

### Post by chili555 on 2015-12-16
Yes, that is correct. On a NUC, without a DVD drive, you will need to install it from a USB.

---

### Post by jules6 on 2015-12-16
Thanks, I have downloaded this image onto a USB:
debian-7.9.0-amd64-netinst
Is that OK?

---

### Post by chili555 on 2015-12-16
Debian? Why not Ubuntu? I and I suspect most of us here, know little about Debian.

---

### Post by jules6 on 2015-12-16
Thanks, I have downloaded this image onto a USB:
debian-7.9.0-amd64-netinst
Is that OK?
Please see PM

---

### Post by jules6 on 2015-12-16
Sorry, I know I am a novice. What is the difference?
Or can you send link for what you think I should install please?

---

### Post by jules6 on 2015-12-16
Is this what I need?

[http://www.ubuntu.com/download/server/thank-you?country=GB&version=15.10&architecture=amd64](http://www.ubuntu.com/download/server/thank-you?country=GB&version=15.10&architecture=amd64)

---

### Post by chili555 on 2015-12-16
> **jules6 said:**
> Is this what I need?

[http://www.ubuntu.com/download/server/thank-you?country=GB&version=15.10&architecture=amd64](http://www.ubuntu.com/download/server/thank-you?country=GB&version=15.10&architecture=amd64)Exactly correct.

---

### Post by jules6 on 2015-12-16
Please see PM

---

### Post by chili555 on 2015-12-16
> **jules6 said:**
> Please see PMI have replied. Please ask any question you want here on the forum so that others may see the solution and benefit.

---

### Post by jules6 on 2015-12-16
I understand of course.If I start now can you help me through this please?

---

### Post by chili555 on 2015-12-16
Go ahead, however, this is probably all you need to know: [http://www.ubuntu.com/download/server/install-ubuntu-server](http://www.ubuntu.com/download/server/install-ubuntu-server)

---

### Post by jules6 on 2015-12-16
I have got a small problem I only have a HDD in a USB docking station. I have loaded ubutnu installation on there but while installing it keeps looking for a CD/DVD drive.
Cannot go any further. Is there another way I can install this?
My HDD docking station can take the HDD from my NUC PC can I install from there?

---

### Post by chili555 on 2015-12-16
I don't understand. I thought you were installing Ubuntu Server on the NUC. Is that correct? Doesn't the NUC have an internal drive, an SSD perhaps?

Mrs. Chili and I are off for a few hours, I'll check back later.

---

### Post by jules6 on 2015-12-16
Yes it does,
How do I get the files onto it though?

---

### Post by chili555 on 2015-12-16
Have you downloaded the server iso and created a bootable USB? If so, insert the USB in one of the USB ports, reboot and go into the NUC's BIOS and select 'Boot USB Devices First' and let it run.

---

### Post by jules6 on 2015-12-16
My usb stick does not seem to work, I am trying to use a usb HDD docking station with a normal HDD instead to install to NUC.
Keep getting "looking for CD rom" message all the time though

---

### Post by chili555 on 2015-12-16
>  I am trying to use a usb HDD docking station with a normal HDD instead to install to NUC.This is well beyond my limited expertise. I suggest you ask here: [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

### Post by jules6 on 2015-12-16
Thanks M8,
 I think the best thing is for me to get another usb stick, That should solve it. 
I will get one and get back to you if thats OK?

---

