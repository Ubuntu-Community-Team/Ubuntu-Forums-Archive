---
title: "Wireless Baby Steps"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by diamond on 2005-11-26
I'm a first-time Ubuntu user running 5.10, and so far I'm very impressed. The one thing that's giving me trouble is, of course, wireless networking.

I have a Dell Inspiron 600m with the 1350 WLAN card. My WAP is the Actiontec GT701 router that came with my Qwest DSL service. I understand I'm not the only one who's had trouble with this.

After much struggling and gnashing of teeth, I got the Broadcom WinXP driver runnin under ndiswrapper, and it claims that it has a good wireless connection. However, when WEP is enabled (no WPA support, I assume), it can't get an address from the router. Without encryption, I can get an address, but the Actiontec router screws up the DNS servers, giving its own address as the first nameserver. I can then ping IP addresses in the outside world, but anything requiring name resolution is so slow as to be completely useless.

What's my next course of action? Obviously I need to fix the DNS problem first (even if that requires getting a new router), but I would also REALLY like to get encryption working again. I don't like having a wide open network. Any suggestions? I tried entering the key several times -- I even typed it in the text editor first and pasted it into the setup box to make sure I hadn't made any typos. Should I have spaces or colons between the hex value pairs, or should it just be one long string?

Thanks for the help; I hope to get this resolved soon.

---

### Post by Lambert on 2005-11-26
I know very little about this router but is there a way to access it and change the dns settings in the router it's self?

And I take it you've looked in /etc/resolv.conf to make sure it was correct.

You may want to look at an app called resolvconf. It's in the repositories. After you download, find the readme doc and go through it. Should be in /usr/share/docs/

---

### Post by diamond on 2005-11-26
Update:

The DNS problem seems to be solved (for now, at least).  I manually set the DNS servers on the laptop and when I restarted, it remembered my settings.
(To answer your question, I have tried manually setting the DNS servers in the router itself. It still does the same thing -- even in Windows. I've talked to the folks at my ISP, and they're at a complete loss as to how to deal with this.)

Just to keep things simple, I Ubuntu to request a static IP address from the router. When I check my network stats, it says it has the IP address (the same one I set), but I still can't ping anywhere -- not even the router itself.

Does this sound like a WEP issue, or could it be something different?

---

### Post by diamond on 2005-11-26
Update Part 2:

It's definitely an issue with WEP. I turned it off, and now I'm online with Ubuntu.

So does anyone have any advice on this?

---

### Post by Lambert on 2005-11-26
There have been many postings on problems with wep it seems. And I'm wondering if it's in the format of the interface file. Here are some examples of setting the key.

wireless-key 0123-4567-89   
wireless-key [3] 0123-4567-89 (if you can specify a certain key such as key # 3 here)
wireless-key s:password [2] (if using an ascii key use this [2] identifies key #
wireless-key restricted [3] 0123456789 (same as above except it addes restricted setting)

You can try playing with these in the /etc/network/interface file.

Are you using an open or shared setting? I recommend open. If you're using an ascii key make sure the key starts with the s:xxxx

---

### Post by bruce147 on 2005-11-26
I had some struggles with my laptop that were posted here in another thread. WEP was one of the problems towards the end. I don't think the System/Admin/Networking problem works (my belief). 
One thing that helped me was to download the program gtk wifi (I used windows and then moved it over to Ubuntu). This is mentioned towards the bottom of WirelessTroubleshootingGuide that Lambert mentioned above. The guide is helpful too.
However, I think if I had studied [http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)
(Debian Network Configuration), particularly 10.6.1.3 Configuring a Wi-Fi interface, that could have helped me through the overall process. I think it might help you.

---

### Post by akniss on 2005-11-26
[QUOTE=diamond]I'm a first-time Ubuntu user running 5.10, and so far I'm very impressed. The one thing that's giving me trouble is, of course, wireless networking.  I have a Dell Inspiron 600m with the 1350 WLAN card. My WAP is the Actiontec GT701 wireless gateway that came with my Qwest DSL service. I understand I'm not the only one who's had trouble with this.
[/QUOTE]

That sounds very familiar.  I too have been a Ubuntu user for less than a month, and also have a Dell Inspiron 600m with Qwest DSL with the 701 gateway.  It just so happens that I finally got my wireless working today with WEP (64bit) enabled.  Here's how I did it:  

1) I followed instructions from this thread to get to the point that I could get online with my laptop wired to the gateway via ethernet cable.
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=244026&highlight=actiontec+wireless+gateway](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=244026&highlight=actiontec+wireless+gateway)
In a nutshell:
1) find your DNS #s
2)edit resolv.conf to match:
```
sudo gedit /etc/resolv.conf
```
Mine looks like this:

search domain.actdsltmp
nameserver 205.171.3.65
nameserver 205.171.2.65

3) Copy the contents to a new file called resolv2.conf:
```
sudo cp /etc/resolv.conf  /etc/resolv2.conf
```

4)Open the bootmisc script
```
sudo gedit /etc/init.d/bootmisc.sh
```
and add the following line to the end of the file:

cp /etc/resolv2.conf /etc/resolv.conf

This should get to the point that you can consistently get to the internet when 'wired'.  Thanks to the folks at linuxquestions.org for getting me this far.

Now comes the expensive part... I tried for a couple weeks to get the wireless working with no luck.  So I bought a D-Link wireless router (DI-524) at Target for $29.99.  I changed the Actiontec IP to 192.168.10.1, then plugged the D-Link router into the ethernet port on the Actiontec gateway.  I could then configure the D-Link's ESSID and WEP with no trouble at all.  My wife still uses the Actiontec wireless with Windows, and I connect to the D-Link with my Ubuntu Laptop.  This is probably not a recommended workaround, but it has worked for me and after two weeks of banging my head, the $30 extra router was a bargain!  I hope this helps.

---

### Post by diamond on 2005-11-26
Thanks for the info, akniss. I figured someone else would have the same setup I do.

You seem to have confirmed my suspicion: the fault is with the Actiontec router, and nothing can be done about it. Leave it to Qwest to choose the shoddiest, biggest POS router to bundle with their service.

I'm shopping around now to see if I can find another DSL router/modem with wireless that will also work with Qwest's service. If I find one, and can get it to work, I'll post an update here. Might make things simpler for you.

In the meantime, I have at least disabled SSID broadcast and enabled the MAC filter so my house doesn't scream "COME HERE FOR FREE ANONYMOUS INTERNET!"

---

### Post by akniss on 2005-11-27
yeah... there are threads about this modem on almost every distro's community pages... and all have various "fixes" that work for peter but not for paul, and I've not seen one yet that has gotten wireless working consistently. I've been working at it since I first installed linux a few months ago (mandrake) and then started again a couple weeks ago when I tried Ubuntu. The kicker is that the modem itself runs a version of linux, but is one of the least linux friendly pieces of equipment.  This is definately not a Ubuntu problem, or even a linux problem; its an actiontec problem, and one that they are not even remotely interested in fixing or acknowledging.

---

