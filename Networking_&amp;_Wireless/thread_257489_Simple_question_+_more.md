---
title: "Simple question + more"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by Mazehero55 on 2006-09-14
I'm having so much trouble getting certain hardware to work that I've decided to just buy new hardware. The only things are a modem and grfx card.

But the modem is most important. 
Do all external modems work in linux or just most?

And if you could,it would be great to suggest a modem, that would work almost perfect right off the batt.I'm going for something cheap that works so; internal is best but I know from experience that those are a pain, but if there is an internal one that works good with Ubuntu the please tell me. You don't have to suggest something if you don't want to but that would help alot.

Edit: oh a Dial-up modem. cable and dsl can't reach me.

Thank you so much!!

---

### Post by moore.bryan on 2006-09-14
*check [http://www.linmodems.org/](http://www.linmodems.org/) for their suggestions if it's a dial-up modem... ubuntu works better with dsl/cable, though; so if it's an option...*

---

### Post by Mazehero55 on 2006-09-14
> **moore.bryan said:**
> *check [http://www.linmodems.org/](http://www.linmodems.org/) for their suggestions if it's a dial-up modem... ubuntu works better with dsl/cable, though; so if it's an option...*

I don't understand what is what at that site. If you don't want to answer then don't, but I would greatly appreciate the help. I have looked at the site, and still not sure where you go there to find a list of modem chipsets that already work with linux.

---

### Post by tbonius on 2006-09-14
I believe he did answer your question.. a very specific answer to a very vague question.  What chipset is your modem?

lspci -V

Does the modem show up in your "Network" options?  

Most PCI card modems that ship today are going to be 3-com, Agere, or Intel based chipsets.  Knowing this information would help in resolving your issue.

T

---

### Post by Mazehero55 on 2006-09-14
:rolleyes: Naw the thing is I need to buy a modem, not fix one. I wasn't saying he wasn't helping me, he just didn't answer my questions. The linmodems place is mostly on fixing modems, and when I click on a modem list, it's filled with broken links. And it doesn't talk about external modems at all.

The one I had was intel based but it sucks and won't work nomatter what I do. I've downloaded the driver(and compiled it) and folowed multiple how-to's but to no prevail. So I just need to know what modems will work without much configuration.
Here's the basics of what I need.

I need a dial-up modem.

So do all external modems work perfect?

Is there an internal modem that works near perfect, if so what is it?

thanks, sorry for the confusion

---

### Post by tbonius on 2006-09-14
If you have an external modem, there is a good chance it works.  Try accessing the modem via the serial port directly (/dev/ttyS0 /dev/ttys1.. etc..)  You can use try passing AT commands to the modem directly to see if you get any output from the modem.  Check /etc/ppp for more information (man pppd)

T

---

### Post by Mazehero55 on 2006-09-14
> **tbonius said:**
> If you have an external modem, there is a good chance it works.  Try accessing the modem via the serial port directly (/dev/ttyS0 /dev/ttys1.. etc..)  You can use try passing AT commands to the modem directly to see if you get any output from the modem.  Check /etc/ppp for more information (man pppd)

T
So I just plug in the external modem and try diferent ports? Thats it? I don't have one yet. So should I get usb or serial port modem, does it make a difference? I heard USrobotics were good ones, should I get one of those. And is there a way I can tell if it works before I buy it?

thanks tbonius

---

### Post by moore.bryan on 2006-09-15
*the linmodems site has a page devoted entirely to those modems which are linux-user-friendly, that's why i gave it to you... it even used to have a page entitled something like "the linmodem you should buy."  my experience with internal modems (winmodem or linmodem) is that they're hit-and-miss.  if you search around the net, you'll see thousands of pages written by people who have been successful with x modem... i think you're looking for a "buyers' guide" and there really isn't one.*

---

### Post by stlscriptmeister on 2006-09-22
At this time I can't tell you precisely which modem you should purchase. However, I can help you narrow your search list a little: (1) US Robotics "Performance Pro" Data/Fax Modem (Model# 5610-B), (2) MultiTech MT5634ZPX-PCI-U "World" V.92 Data/Fax Modem. These are both controller-based internal (PCI) modems. And that is the key, these are "hardware" (read: "real") modems, and not "winmodems".

Like you, I am doing my "due diligence" research before selecting and buying a dialup modem. Both of the above are internal (PCI slot) modems. I would prefer an internal modem simply because they don't take up any additional desk space. If you really want to play it safe, then you should look around for a serial-attached (RS232 not USB) external modem. According to what I have read (this is from my research, NOT my personal experience) external serial modems are practically the ONLY ones that will work effortlessly with Linux (Ubuntu and other Debian derivatives included).

I would certainly be interested to hear from anyone out there who has installed a US Robotics Performance Pro or MultiTech MT5634ZPX and gotten it to work with Ubuntu 6.06 LTS (Dapper Drake), wouldn't you?     :?:

---

### Post by acefreely on 2006-09-22
Go with an external serial port modem, which is a real hardware modem.  Most of the PCI modems are software based (unless you can still get ISA modems and you have ISA slot).

Something like this would be guaranteed to work...
[http://www.usr.com/products/home/home-product.asp?sku=USR5686E]("http://www.usr.com/products/home/home-product.asp?sku=USR5686E")

If it's external and serial port, it'll work in Linux.  I have yet to find one that doesn't...PCI based on the other hand can be a pain.  If you find a cheap one PCI modem that you want, google the chipset and see if you can find anyone using it in Linux.

---

