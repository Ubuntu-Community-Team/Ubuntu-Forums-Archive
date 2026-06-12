---
title: "DLNA not working at all"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by d-lhoest-y on 2014-05-13
Hello all of you.

I do not understand what is going wrong with my computer and DLNA.

I have a Dell Inspiron 14z machine with Ubuntu 13.10 64bits. I have been trying to use at as a DLNA device but nothing works.

I have tried MiniDLNA, MythUbuntu, MediaTomb, BubbleUPnp, Plex, Ushare, ... Opened the necessart ports using gufw but still, nothing works.

I spent ours on forums and tutorials and everything I did was as explained.

I am now desperate... 

Thank you in advance for your help

---

### Post by Vladlenin5000 on 2014-05-13
Opening local ports is useless if those ports aren't available at the router. Probably you check just that before trying one software after another...

And please describe exactly what you are trying to achieve, whether you want that machine to be a server, client or both... What are the other devices involved and how are you testing...

---

### Post by d-lhoest-y on 2014-05-13
Good point, I indeed did not think of that... I am trying to turn my computer into a server in order to stream my media on my PS3, tablet,...

---

### Post by matt_symes on 2014-05-13
Hi

> **d-lhoest-y said:**
>  Opened the necessart ports using gufw but still, nothing works.

You have a firewall enabled on your server ?

Did you allow the SSDP Packet ?

How's about posting your firewall rules here.

Have you looked (using tcpdump or some-such) to see what packets are reaching/leaving your server ?

Mediatomb runs peachy on my server.

Kind regards

---

### Post by d-lhoest-y on 2014-05-14
Good afternoon, 

Thank you for your answers, food for thoughts. I realised the prequesites were not fulfilled as yet (for instance, Upnp was not yet installed...)

---

### Post by HiImTye on 2014-05-14
is UPnP enabled on your router?

---

### Post by d-lhoest-y on 2014-05-14
Hello again, I will try to give you the necessary details.

I am not using an Ubuntu server but my personal laptop.
UPnP is enabled on the router and ports are opened as per the software requires (both Mediatomb and MiniDLNA).

---

### Post by HiImTye on 2014-05-14
do you see the DLNA shares if you browse in, for instance, totem?

---

### Post by whereismymindat2 on 2014-09-09
> **d-lhoest-y said:**
> Hello all of you.

I do not understand what is going wrong with my computer and DLNA.

I have a Dell Inspiron 14z machine with Ubuntu 13.10 64bits. I have been trying to use at as a DLNA device but nothing works.

I have tried MiniDLNA, MythUbuntu, MediaTomb, BubbleUPnp, Plex, Ushare, ... Opened the necessart ports using gufw but still, nothing works.

I spent ours on forums and tutorials and everything I did was as explained.

I am now desperate... 

Thank you in advance for your help

________________________________________

I am brand new to Ubuntu, thus this is not "Ubuntu Advice" however one way I learned the hard way setting up a DLNA server. Ironically seems *MYSELF INCLUDED* over complicated it. 
Meaning, spending too much time preparing a Render/Server without taking into account with File Types necessary for your T.V. to recognize. 
Remember, DLNA is designed to be "Soccer Mom" friendly (aka Iphone/AOL  friendly)
 ---This is why was driving me NUTS trying "to fix". ( what frustrated me to no end). :wink:

The fact you are using rather "Trustworthy"/"Robust"/"Respected" Servers (Dead on with Plex).
Your suggestion of trying all the "Good Servers" Makes be believe the  files you are trying to stream are not the correct format for Samsung. 



I use an LG
[http://www.lg.com/levant_en/support/product-help/doc-1350493043578-en-LGELF](http://www.lg.com/levant_en/support/product-help/doc-1350493043578-en-LGELF)
The supported file types are (mostly "Usual Suspects")

[TABLE]
[TR]
[TD="align: left"][FONT=Trebuchet MS][COLOR=#000066]**Codec**[/COLOR][/FONT][/TD]
[TD="align: left"][FONT=Trebuchet MS][COLOR=#000066]**File extensions (Container)**[/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][FONT=Trebuchet MS][COLOR=#000066]MPEG2 [/COLOR][/FONT][/TD]
[TD="width: 492, align: left"][FONT=Trebuchet MS][COLOR=#000066]DAT, MPG, MPEG, TS, TRP, VOB, MKV, DivX, AVI[/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD="width: 40, align: left"][/TD]
[TD="width: 117, align: left"][FONT=Trebuchet MS][COLOR=#000066]MPEG4[/COLOR][/FONT][/TD]
[TD="width: 492, align: left"][FONT=Trebuchet MS][COLOR=#000066]MP4, MKV, DivX, AVI[/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD="width: 40, align: left"][/TD]
[TD="width: 117, align: left"][FONT=Trebuchet MS][COLOR=#000066]H.264[/COLOR][/FONT][/TD]
[TD="width: 492, align: left"][FONT=Trebuchet MS][COLOR=#000066]TS, TRP, MP4, MKV, DivX, AVI[/COLOR][/FONT][/TD]
[/TR]
[/TABLE]

I was beating my head on my desk for days not knowing what was wrong.The DVD's I "backed up" to my Hard drive, I used VOB format, stripping through VLC
What I failed to do is **roll them into a Container. **
edit/
Thus using Handbrake I rolled into a Container. (FYI_Handbrake is a transcoder ONLY it won't allow you to back up the DVD to your hard drive). 

*IF* this is the case for your solution, I would suggest you view the file type you have in your repository, and use "Handbrake" if you need to foll into a container. 
[https://handbrake.fr/](https://handbrake.fr/)   (fyi---it *is* in the Synaptic Repository for easy install). 

Not sure  how comfortable you are Technically 
Handbrake is rather "bare"---it's just a GUI / barely layered a-top command line/ type release (yet to even make it to a 1.x release). 
However with 15-20minutes of patience will be up to speed . 

Great Product. This will save hassle of having to recreate your back ups *AND* learn new trans-coding techniques to boot! :-)

___________________________


Here is a longer list (note the "Cross Platform" solutions. Don't bother reading too many reviews--most are opinion based only. (misses this/has that). 
[https://en.wikipedia.org/wiki/List_of_UPnP_AV_media_servers_and_clients](https://en.wikipedia.org/wiki/List_of_UPnP_AV_media_servers_and_clients)

___________________________
 

Best of Luck!
WSMMAT


PS-What I should also suggest (if you are on a network---just for throwing spaghetti against the wall, I would Hard Wire your/Ethernet Card / to  Lapttop to the Router the T.V. is on
This eliminates any Wi-Fi set up issues which is another fun experience.

If you just *HAVE TO* start watching (LG at least) offers to USB devices if you have a USB FOB--you can load it up with that, slip into back of T.V. 

Best! :-)

---

