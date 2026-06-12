---
title: "Uuuugh. ICS problems...."
date: 2005-11-10
forum: Networking &amp; Wireless
---

### Post by eddorey2k3 on 2005-11-10
Hey and what-not.

Story so far.

I was originally running FC4. Got told Ubuntu had better support, so I installed Ubuntu. I was trying to get my broadband working, but decided with some help that was going to be a no-go.

Anyway. I had the "bright" idea of using a crossover cable to share it today! I found a guide, on here, from....someone, no idea who, and was following it. Alas, at the stage his said "That's it." mine was still not working.

So, what I need is someone to help me go through it, and try and point out what could be wrong with it.

I really don't want to give up on Linux yet, but a stand-alone box is pretty pointless.

Oh. If you have msn, and would be willing to give me your (msn) address, it'd be helpful.

Thanks a lot.

Ed.

[Edit: Details of what i've done so far can be provided if needed, as well as current problem]

---

### Post by matthew on 2005-11-10
Hey

Take a look at this:
[http://ubuntuforums.org/showthread.php?t=76346](http://ubuntuforums.org/showthread.php?t=76346)

It isn't the exact same thing you are trying to do, but it is close and migt give you some good ideas of where to go first and how to head in the direction you want to go.

---

### Post by eddorey2k3 on 2005-11-10
Ok. I followed that up to point 4, but due to the fact it's a windows machine, I can't finish it.

What would you suggest?

---

### Post by eddorey2k3 on 2005-11-10
Ok. A quick update. I can now ping the Ubu. box from Windows, and vice versa. The ubu. box also responds very quicky, but I guess it's to be expected.

I can't get on any websites with the Ubu. box, without using the IP or the URL. This leads me to think there is something wrong with either the DNS, or the ICS?

---

### Post by matthew on 2005-11-10
You are really close now, but just beyond where I can help out with specific instructions. I don't use windows and I don't have access to a windows computer to explore so I can't tell you exactly where to find out the information you need. 

In relatively plain English what you are looking for from your windows machine is the IP address it is using to access the internet nameservers. What nameservers do is translate the nifty names we use for web page addresses and such into proper numerical IP addresses. For example, [www.google.com]("http://www.google.com") translates to 216.239.37.99. Instead of us having to memorize all the numerical addresses there are computers out there that exist just to do this for us. You need to find out which one your windows computer uses so that the other computer connecting through it can be set up to use the same one. (really this comes from your internet provider, but windows must have a record of it somewhere...maybe in the networking setup area?)

EDIT: I know that paragraph was a bit remedial, but someone else may read this later and not know that important bit of background info.

If anyone knows where this info is found on windows and can post and help eddorey2k3 get set up it would be appreciated.

---

### Post by eddorey2k3 on 2005-11-10
You can get this information from opening a command prompt (Start > Run > cmd.exe) and typing "ipconfig /all" and that displays a list of the DNS servers being used.

Is this the information I need?

---

### Post by matthew on 2005-11-10
[quote=eddorey2k3]You can get this information from opening a command prompt (Start > Run > cmd.exe) and typing "ipconfig /all" and that displays a list of the DNS servers being used.

Is this the information I need?[/quote]Most likely. Try it and see if it works.

---

### Post by eddorey2k3 on 2005-11-10
What am I doing with it? 

For reference, the info is: Primary DNS:    194.72.0.98
                                   Secondary DNS: 194.72.65.68

---

### Post by matthew on 2005-11-10
[quote=eddorey2k3]What am I doing with it? 

For reference, the info is: Primary DNS:    194.72.0.98
                                   Secondary DNS: 194.72.65.68[/quote]
On your Ubuntu computer go to a terminal and type
```
sudo gedit /etc/resolv.conf
``` The file is probably empty or may not even exist currently. In any case, if there is something there, erase it and put this in
```
 nameserver 194.72.0.98
 nameserver 194.72.65.68
``` then save and exit gedit.

Now test it. Open firefox and type something simple in the address bar like "www.google.com"
  
  If we did everything right it will work.

Here's the catch: the resolv.conf file will be regenerated every time you reboot so unless you enjoy recreating the file each time we need to make it permanent.
  
  While the current internet connection is working, with all the [extra repositories enabled]("https://wiki.ubuntu.com/AddingRepositoriesHowto"), fire up synaptic or apt-get install **resolvconf**
  
  Once that is installed

       [LEFT]```
cp /etc/network/interfaces /etc/network/interfaces_backup
gedit /etc/network/interfaces
```[/LEFT]
       
   and add the following to that file under the heading shown using the information from your current, working /etc/resolv.conf:

       
```
iface eth0 inet static
[LEFT]   dns-nameservers 194.72.0.98 194.72.65.68[/LEFT]
 
```[LEFT]
[/LEFT]
      This will automatically create your (correct) /etc/resolv.conf file every time you reboot.

---

### Post by eddorey2k3 on 2005-11-10
God damn. It doesn't work. It's not picking up the names properly. It just sits there, with "Looking up www.google.com" and ping gives "Unknown host".

What do you suggest we try now? >_<

---

### Post by matthew on 2005-11-10
[quote=eddorey2k3]God damn. It doesn't work. It's not picking up the names properly. It just sits there, with "Looking up www.google.com" and ping gives "Unknown host".

What do you suggest we try now? >_<[/quote]Stink. I was certain that would do it. I'm just about to sit down to dinner and then spend some time with my kids before they go to bed. I will let the problem simmer at the back of my mind for a while. Hopefully something will come to me or maybe (please!) someone else will jump in here with some thoughts/ideas.

---

### Post by matthew on 2005-11-10
After some time away and some thought I have some areas to explore that could be causing problems. Since you said you can ping without errors between the two computers then it seems the problem must be in how the packets are flowing to/from the internet at large through the Windows computer.

Does the Windows computer have a firewall? Is it blocking access from the Ubuntu computer to the internet?

Have you enabled port forwarding on the Windows computer? This is what allows packets coming to/from the Ubuntu computer to flow. 

As I mentioned earlier, I don't know how to do this in a Windows environment, but this may be the key to your problem.

---

