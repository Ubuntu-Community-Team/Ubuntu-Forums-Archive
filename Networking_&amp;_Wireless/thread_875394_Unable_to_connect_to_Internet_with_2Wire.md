---
title: "Unable to connect to Internet with 2Wire"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by TheHackMan on 2008-07-30
I have been having some very annoying trouble while trying to wirelessly connect to the internet on my laptop. There are several things that seem to be going on:
1. At random for about 2 seconds I can connect to the internet before it stops working. Via manual configuration I open it, check the box to enable the wireless connection, click on close, and about 45% of the time a web page will load and then the internet dies and upon opening up the manual config again I notice that its then unchecked itself(this is 5% of the time)
2. About 95% of the time however when I check the box to enable wireless, click close and try to access a webpage nothing loads, and when I reopen the manual config box the box for wireless internet is still checked
3. I have been able to connect to the internet wirelessly at my dads house. He has a Linksys router but at my moms house(where the problems are) she has a 2WIRE HomePortal 1800HW
4. At my dads house I have to enter the DNS information of the ISP to get to the internet not the IP address of Linksys router(192.168.1.1) 
5. At my moms house 2WIRE configures the wireless to use the router as the DNS(via the IP 192.168.1.254) instead of using the ISP DNS info(The DNS info is auto changed when I connect via a wired connection).
6. The connection never seems to last for more than two seconds before it dies
7. The two second spurts of internet have happend when I put in the two DNS servers of the ISP and with I put in the IP of the router as the DNS server
8. Under manual configuration when I go to select the Network Name from a list the SSID of the router DOES show up 100% of the time

---

### Post by TheHackMan on 2008-08-01
Well I just managed to solve the problem. I gave up on trying to get the wireless to go through the 2WIRE router and got a TRENDnet router and after some hassle correctly daisy chained the two together and now have the wireless going through the TRENDnet router, disabled wireless on the 2WIRE, and have working wireless internet that way. I know its a bit of a hassle but its working and I got added wireless security so in a way its good(now using WPA key with MAC address filtering).
-Problem Solved-

---

### Post by iacobus on 2008-08-01
I have the same problem with my 2Wire HomePortal 1000HW, except that whenever I try to connect to it it crashes and kicks everyone off the network, even if they were wired to it.  Still haven't figured out how to make it work.

.:iacobus:.

---

### Post by choka on 2008-09-24
I have the same problem, I was using Gutsy and I had to install the wireless driver manually so everything worked fine there... Now  I decided to move to "Linux Mint Elyssa" (which is basically Hardy) and now I can connect to some 2wire routers I was able to connect before, and in some cases it completely resets the router while I'm trying to connect. Also the wireless led on my laptop doesn't blink...

I found similar bug reports but no answers... and this happens only with some specific models of the 2wire routers... :confused::(:mad:

---

### Post by acreech on 2008-11-12
I have a 2wire router and have never been able to connect to it with hardy or intrepid. I have a second laptop with Windows XP OS. That computer can connect to the 2wire without issues. I prefer to use the ubuntu computer, but can't seem to get over this wireless issue.

---

### Post by acreech on 2008-11-16
> **acreech said:**
> I have a 2wire router and have never been able to connect to it with hardy or intrepid. I have a second laptop with Windows XP OS. That computer can connect to the 2wire without issues. I prefer to use the ubuntu computer, but can't seem to get over this wireless issue.

I just finally got my computer to connect to my wireless after 4 months of trying to connect to my own wireless router. I found on my wireless router settings there is "Mac Filtering". I disabled the Mac Filtering and the computer connected to my 2wire router. 

So check your settings for the Mac Filtering and then disable it.

---

### Post by 081105jk on 2008-11-16
2005&#24180;&#20844;&#21496;&#25104;&#31435;&#20043;&#21021;&#65292;&#21363;&#20197;&#25972;&#21512;&#32593;&#36890;&#21644;&#30005;&#20449;&#12289;[**&#32593;&#32476;&#30005;&#35805;**](http://www.71168.org/)&#38081;&#36890;&#31561;&#22522;&#30784;&#36816;&#33829;&#21830;&#30340;&#20248;&#21183;&#36890;&#20449;&#36164;&#28304;&#20026;&#37325;&#24515;&#65292;[&#32593;&#32476;&#30005;&#35805;](http://www.71168.org/)&#20805;&#20998;&#21033;&#29992;&#39640;&#25928;&#30340;&#25968;&#23383;&#23485;&#24102;&#32593;&#32476;&#25216;&#26415;&#65292;[**&#32593;&#32476;&#30005;&#35805;**](http://www.71168.org/)&#20943;&#36731;&#24191;&#22823;&#20225;&#19994;&#29992;&#25143;&#30001;&#20110;&#20256;&#32479;&#30005;&#35805;&#36164;&#36153;&#39640;&#26114;&#25152;&#24102;&#26469;&#30340;&#27785;&#37325;&#36127;&#25285;&#65292;[**&#32593;&#32476;&#30005;&#35805;**](http://www.71168.org/)&#20197;&#21450;&#20026;&#26377;&#24535;&#20174;&#20107;&#32593;&#32476;&#30005;&#35805;&#32463;&#33829;&#39033;&#30446;&#30340;&#20154;&#22763;&#25552;&#20379;&#21019;&#19994;&#26426;&#36935;**&#12290;[&#32593;&#32476;&#30005;&#35805;**[/url]&#20844;&#21496;&#29575;&#20808;&#24341;&#36827;&#22269;&#38469;&#39640;&#31471;&#30340;SIP&#25216;&#26415;&#65292;&#22312;&#20197;&#21271;&#20140;&#20026;&#36752;&#23556;&#30340;&#21508;&#21608;&#36793;&#22320;&#21306;&#24314;&#31435;&#26381;&#21153;&#32593;&#28857;[**&#32593;&#32476;&#30005;&#35805;**](http://www.71168.org/)&#65292;&#21463;&#29702;&#32593;&#32476;&#30005;&#35805;&#23433;&#35013;&#19994;&#21153;&#24182;&#38754;&#21521;&#20840;&#22269;&#24449;&#38598;&#19968;&#32423;&#20195;&#29702;

---

### Post by nu2this2 on 2008-11-16
> **acreech said:**
> I have a 2wire router and have never been able to connect to it with hardy or intrepid. I have a second laptop with Windows XP OS. That computer can connect to the 2wire without issues. I prefer to use the ubuntu computer, but can't seem to get over this wireless issue.
 

I have a 2-wire router and found the Edimax EW-7128G PCI Wireless Card to work perfectly right out of the box using Hardy. I bought it from Newegg.

---

### Post by acreech on 2008-11-16
My router would have worked out of the box for me too, but I did not know that the mac filtering was only allowing listed computers to connect to my wireless router. I had set the router up when I had Windows XP and obviously forgot about that setting, and then never thought to go back and look at that setting again.

---

