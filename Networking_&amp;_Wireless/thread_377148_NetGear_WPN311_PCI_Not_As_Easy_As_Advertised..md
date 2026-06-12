---
title: "NetGear WPN311 PCI Not As Easy As Advertised."
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by Carewemust on 2007-03-05
Hello Everyone,

I talked my wife into letting me put Xumbuntu on my 11 year old son's computer this past weekend, because Microsoft wanted $99 to upgrade his 2000 Dell from WIN98 to XP. 

Getting the Xubuntu image burned onto a CD using another computer and then putting it on my son's PC was simple enough. Very easy. But for the past 3 days I've been pulling my hair out trying to get his computer online to our home network. Three days ago, I found this link here in the Ubuntu support area: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear) , so I went to Best Buy and purchased a NetGear WPN311 PCI Desktop Card and installed it in his PC. This community document says that the NetGear WPN311 is one that would work "Right Out of The Box", but I get the feeling that there's something else I need to do, because Linux's "Right Out of The Box" doesn't seem to mean the same thing as Windows "Plug and Play". I've read several topics here that talk about an NDSWrapper, Typing Commands into some kind of Terminal, etc.. The LinkSys USB thing that I had plugged into the back of his computer worked great with Windows98/XP, but not with Linux, which is why I purchased the NetGear WPN311.

I have roughly 36 hours to get Nathanael's PC onto our home Network, or my wife is going to cough up $99 and force me to convert back to WinXP. I really would prefer not to do this, but I'm getting fatigued. Is there any manual which shows SCREEN SHOTS of the steps for getting a Linux compatible PCI Card online with a home network? Pictures are worth a thousand words to those of us who just need to get a job done quickly. Any help is appreciated. -Bert in Chicago

p.s. I just visited the NetGear Site and see that the WPN311 is only compatible with WINDOWS operating systems.
[http://www.netgear.com/Products/Adapters/RangeMaxAdapters/WPN311.aspx](http://www.netgear.com/Products/Adapters/RangeMaxAdapters/WPN311.aspx)
Should I take it back and get another one?  I hope whoever keeps that Wireless Hardware Compatibility page  up to date will
correct the misleading statement about the NetGear WPN311.  It is not as simple and plugging it into the PCI slot and entering
the SSID into the Networking section of Xumbuntu.

---

### Post by kaicrr77 on 2007-05-07
Hello Carewemust,


I just installed this card on Feisty. It will work out of the box. Now considering you are accessing these boards first thing i recommend is that you pick up this little applet. 

[http://ubuntuforums.org/showthread.php?t=18466&highlight=wireless]("http://ubuntuforums.org/showthread.php?t=18466&highlight=wireless")'> 

Using this applet will make things A LOT easier as the default network manager for Gnome blows as it doesnt' update your setting changes properly (at least for me) when it comes to wireless. Also this is a lot prettier IMO. 


If you can't get a hold of this applet then try this:

First on the router you need to turn on WEP - 128 -bit encryption. You should do this whether using the applet above or not. You will have to type in your paraphrase (keep it simple) and then generate a key. The generated key is what you will use. Feel free to copy it out of the text box unless you like to type.

Once you have done this, go to "System -> Administration -> Network ". Then highlight your wireless connection and click on Properties.

A window will appear, you will need to un-check roaming mode. Then select your password type "hexadecimal". Now click on the Network Name drop-down. If your router name appears here you are in VERY good shape.  Go ahead and select it. 

Now in the network password box paste in your WEP key. Once you have done this click on "OK".  Wait for it to update your network changes. Then open up Firefox and try to hit a web page. if it doesn't work on first go don't get discouraged. I had to do this maybe 3 times before it took the change. 

However, like i said if you can get the applet I listed above it will make your life a lot easier as it looks just like the Windows XP wireless manager and acts almost the same and will also give you signal strength.

Hope this helps.

Good Luck
-K

---

