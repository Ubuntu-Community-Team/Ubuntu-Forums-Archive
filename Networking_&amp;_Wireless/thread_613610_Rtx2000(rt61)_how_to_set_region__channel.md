---
title: "Rtx2000(rt61) how to set region / channel"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by broomie on 2007-11-15
Folks

I have a happy ubuntu install with an Edimax pci wfi card (rt61/rt2x00) drivers on Gutsy. The channels have defaulted to 1-11 assuming I'm USA and not UK (1-13).
I've always sued channel 13 in the past a this seems best dealing with next door radio baby alarm.

How do I set the Country code (1?) and channel ?

I tried iwconfig wlan0 channel 13 but I get an error telling me that Frequency neds to be set. However this seems incorrect as 54g happil works on 11 (when baby arm not on!)

I tried to look for a tr61xx.dat in /etc/wireless as some post talk about but there is no /etc/wireless.

many thanks

Paul

---

### Post by wieman01 on 2007-11-15
Do you have to set it at all? I think you need to set the channel on the router, that's all. As soon as your clients associates with it via SSID, it should set the channel automatically...

---

### Post by broomie on 2007-11-15
Hello thanks for replying
 
I deliberately set the router to 13 to avoid the baby alarm.

The issue is that the "out-of-the-box" Driver will only recognise 1-11 and not UK 1-13.

Its connects happily 1-11 if WAP router is set to 1-11 but I would like to get the ubuntu pc to use channel 13 and I cannot see a way to do this.

Hope that is a bit clearer and thanks again.

I've read thread where folks in Australia (1-13)fixed this some Unbuntu releases ago with iwconfig but seems this has changed.


Paul

---

### Post by wieman01 on 2007-11-15
Ok, got it.

Please so this from a terminal and post the output. I am sure you will be able to set the channel if you know how to input it correctly (i.e. frequency rathern than channel):
> iwconfig --help

---

### Post by broomie on 2007-11-15
Thanks I'll do that.

To save you the bother of more work (thanks a million BTW) is there a list somewhere that shows

Channel = Frequency

I am at work so I'll do this tonight or at the weekend

much appreciated


Paul

---

### Post by wieman01 on 2007-11-15
> **broomie said:**
> Thanks I'll do that.

To save you the bother of more work (thanks a million BTW) is there a list somewhere that shows

Channel = Frequency

I am at work so I'll do this tonight or at the weekend

much appreciated


Paul
No problems. Post here if you have any results.

Thing is that I believe that you have entered an incorrect numerical value. You need to specify the frequency and in the right format.

---

### Post by broomie on 2007-11-15
Weiman

I am sure you are right 

I tried - the other day" iwconfig wlan0 channel 13" and it said incorrect frequency(not exactly) 

SO I guess its"wconfig wlan0 frequency xxxxkhz?"


thanks again


Paul

---

### Post by wieman01 on 2007-11-15
Yes, you could do:
> sudo iwconfig wlan0 frequency **2.437G**
...for instance. Can't quite remember what the exact frequency but you'll figure it out.

---

### Post by broomie on 2007-11-15
I presume also I should "stop" the service first

thanks


Paul

---

### Post by wieman01 on 2007-11-15
Found it here:

[http://linuxcommand.org/man_pages/iwconfig8.html]("http://linuxcommand.org/man_pages/iwconfig8.html")

>        _**freq/channel**_

              Set the operating frequency or channel in the  device.  A  value
              below 1000 indicates a channel number, a value greater than 1000
              is a frequency in Hz. You may append the suffix k, M or G to the
              value  (for  example,  "2.46G"  for  2.46 GHz frequency), or add
              enough &#8217;0&#8217;.
              Channels are usually numbered starting at 1,  and  you  may  use
              iwlist(8)  to  get the total number of channels, list the avail-
              able frequencies, and display the current frequency as  a  chan-
              nel. Depending on regulations, some frequencies/channels may not
              be available.
              When using Managed mode, most often the  Access  Point  dictates
              the  channel  and  the driver may refuse the setting of the fre-
              quency. In Ad-Hoc mode, the frequency setting may only  be  used
              at  initial  cell  creation,  and may be ignored when joining an
              existing cell.
              You may also use off or auto to let the card pick  up  the  best
              channel (when supported).

             _** Examples :**_
                   iwconfig eth0 freq 2422000000
                   iwconfig eth0 freq 2.422G
                   iwconfig eth0 channel 3
                   iwconfig eth0 channel auto
Yes, stop the service first.

---

### Post by Fab@London on 2007-11-15
Hi,

I'm in the same case. I am not the network manager so, I can't modify the channel of the network.

I've already tried to change the frequence but, on the contrary to the channel setup, it said me nothing but it did nothing too (the frequency was unchanged).

I have looked in several forum but few people deal with this problem ...

PS : sorry for my bad english ... I'm french and there is nothing too in the french forums

---

### Post by broomie on 2007-11-18
Folks 

No luck I am afraid

sudo iwconfig wlan0 freq 2.472    (this is Channel 13 in UK) and I get...


Error for wireless request -set frequency (8b04)

I tried stopping the card but same effect

same issue whatever feq I try - same if I replace freq with "channel" command!


Any help gratefullt received


Paul

---

### Post by Blutack on 2007-11-18
Tried ndiswrapper?
If you use the windows wireless drivers that came with the card they should theoretically support channel 13

---

### Post by broomie on 2007-11-18
Thanks I 'll give that try!

Any pointers  one here there is agood gide to do this?

Also will / how to unintsall the native drivers to make ndis work?

many thanks


Paul

---

### Post by kevdog on 2007-11-18
Just blacklist the rt61pci driver (or whatever driver you are currently running) in the /etc/modprobe.d/blacklist file to prevent it from loading on boot.  If you dont want to reboot, then unload it manually:

sudo modprobe -r rt61pci

---

### Post by wieman01 on 2007-11-18
> **broomie said:**
> Thanks I 'll give that try!

Any pointers  one here there is agood gide to do this?

Also will / how to unintsall the native drivers to make ndis work?

many thanks


Paul
Try the one in my signature...

---

### Post by cmirandamora on 2007-11-21
> **broomie said:**
> Folks

I have a happy ubuntu install with an Edimax pci wfi card (rt61/rt2x00) drivers on Gutsy. The channels have defaulted to 1-11 assuming I'm USA and not UK (1-13).
I've always sued channel 13 in the past a this seems best dealing with next door radio baby alarm.

How do I set the Country code (1?) and channel ?


Paul

I have the same problem and also with baby monitor.

Did you find any good solution?

Thanks.

---

### Post by broomie on 2007-12-10
My solution more of a bodge really...

replaced the Rt61 based card with an £8.00 Atheros based card and it worked a treat!

Channel 13 works

see

[http://www.ebuyer.com/product/123453/show_product_reviews](http://www.ebuyer.com/product/123453/show_product_reviews)

good luck

Paul

---

### Post by MadnessRed on 2008-03-06
I have belkin pci card, trying to connect to channel 13, can you tell me how you got your new card to work please

thanks

---

