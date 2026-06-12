---
title: "Connecting to dial up, help!"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by Kulluminatii on 2006-08-08
I finally recieved the new version of Ubuntu through the mail hoping that this time it would be able to find my modem, but it's the same as last time. 

I've downloaded the file "scanmodem" from this link

link: [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#modems](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#modems)

I do not get what I am supposed to do though. I burnt the file onto a cd, and then copied the files on my computer with Ubuntu on it, i made it run in terminal, nothing showed up.:mad: 

What do I do with the highlighted box?

```
wget -c http://linmodems.technion.ac.il/packages/scanModem.gz 
gunzip -c scanModem.gz > scanModem 
chmod +x scanModem
sudo ./scanModem 
gedit Modem/ModemData.txt
```

It mentions underneath the hightlighted box that I should "Read this file, it should list what modem chipset you have." How in the hell do i read the file?

I've also looked through this link, although it mentions i have to do the above first before im able to continue.

link: [https://help.ubuntu.com/ubuntu/desktopguide/C/internet.html](https://help.ubuntu.com/ubuntu/desktopguide/C/internet.html)

Thank you very much for taking your time to read through all this and hopefully I can get some help and finally get the internet to work on it!:p


***EDIT- ADDITIONAL INFORMATION***

The modem i have in my pc im trying to install ubuntu on is not the original modem, i bought it after the previous one burnt out. 

Here is some information about the modem, maybe something I list might make it easier for you guys to help me.

**Manufacturer**: Archtek
Websites: [www.archtek.com](www.archtek.com)
[www.archtek.com.tw](www.archtek.com.tw)

**Name**: SmartLink

**Features**: Support ITU v.92/v.90 56k protocol
Compliant with PCI 2.1 and 2.2 specification

**Specifications**:

Data Mode
* Maximum Download Speed 56.000bps
*Command Set: TIA/EIA 602 "AT" command set
*Standard: ITU-T V.92, V.90, V.34, V.32bis, V.22bis, V.21, Bell 212A and Bell 103
*Error correction: ITU V.42, MNP 2-4,
*Data compression: ITU V.44, V.42bis, MNP 5
*Operating Systems: Windows 95/98/ME/2000/XP

---

### Post by Kulluminatii on 2006-08-08
Well I am downloading some drivers I just found on the website, i dont even know if they are the ones I need, I just saw that their for Linux and 56k modems, so im praying[-o< 

When I download the drivers, how do I go about downloading them onto Ubuntu itself so it well recognize the modem.

Also, im not sure if this will work, so if you were in the middle of typing something and saw this, please go ahead and post it, because the drivers might not work.:(

---

### Post by Kulluminatii on 2006-08-08
Oh this is the link where I found the drivers, one of them seems like it has more information on it which sort've ran on ubuntu (when I mean sort've ran i mean it didnt give me a "cannot do blah blah blah message")

I think it was this one

  	 Linux (5618PSV)

that worked more, man im confused on what to do ](*,)

I copied the driver file onto the ubuntu pc and just clicked on random files.

---

### Post by Kulluminatii on 2006-08-08
Anyone?

---

### Post by Kulluminatii on 2006-08-08
I used this tutorial on Software Modems
link: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

And it created a Modem folder on my desktop with a bunch of .txt files.


On the guide it says "But after running, you will see a number of new folders, including a 'Modem' folder" all I see is a 'Modem' folder.

Also, this is what really confused me.

"Read read1st.txt and modemdata.txt in there, praying that it recognized your modem."

I read them, err..well not really read, but skimmed through all the words I could make out..am I supposed to get a message it recognized my modem

OR 

Is their a specific part in each .txt file that I am supposed to look at that gives my information on the modem?



Why do I feel like im talking to myself? :-|

---

### Post by Fittersman on 2006-08-09
haha because you are, nobody knows how to fix a modem, i could find nobody to help me with mine either.

---

### Post by nige2007 on 2006-09-30
well ive just took the plunge:( thought why wait ... i should have known i wouldnt be able to simply walk in and surf! install went fine! nota hitch very impressive! but then i thought basics like any newcomer, how to find where to enter my isp details etc dial up number etc oh yeah im on dial up 56k modem 48kbps, hey i thought i must try and see if theres any firewall needed windows burned in brain still need firewall need firewall ...need antivirus...etc:) cant find oh came here found useful info, then more hurdles to overcome   found auto detect modem , pressed it no can find it said!:( so me thinking on feet thought aha!! no modem drivers ...well i thought perhaps stupidly that all the necessaries would be installed on installation, I then spent ages trawling the forums trying to find out stuff and getting more and more bogged down in info ,:confused: yep certainly am , ive rebuilt my thinkpad a20m from bits and pieces Im not working so i thought great way to learn and perhaps better my pc skills, in my previous posts I know how to install and config xp but thought id try unbuntu as i hate ms and there wga even though im a legit xp user:D  I know you have to download and install stuff to enhance linux but i wish someone would make it easier for a newbie to get the basics in easy steps , yes i know holding hands is nice:) :) but remember you too were once a greenhorn , I can download stuff via windows but no dice via the new install on laptop methinks xp calls from behind the sofa) im gonna mess around for a bit before i hoist it off my pc and put xp back ...that is unless i get any answers ...nice ones please]

---

### Post by darth_vader_ca on 2006-09-30
I have always had issues with modems and linux, just make sure its not a winmodem. if it is you need a third party utility like on [http://linmodems.org/](http://linmodems.org/)

cheers.

---

