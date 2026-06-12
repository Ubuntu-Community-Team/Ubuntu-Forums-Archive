---
title: "Live CD v HD Install wireless detection"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by iansl2000 on 2007-01-14
I have booted from the live CD on my main windows XP equiped PC and have connected to my wireless network and therefore the internet with no trouble by using the System>Administration>Network tool. So far so good.

If I now install Ubuntu on my other PC which has no Windows os on it at all, and I fit exactly the same wireless network card as above, should Ubuntu recognise it in the same way as the Live CD version on the windows pc does?

Or is it more complicated than that?

The card is a Belkin F5D7000 and the driver is showing in windows as RT2560
I am using Ubuntu 6.06 LTS

Sorry if this should be in the Newbie section.

Many thanks for any help,

---

### Post by neoroses on 2007-01-14
it should work but i have had a hell of a lot of issues with this card but if it does not work folow one of these guides =) and it will work (which version of ubuntu r u using?)

[http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete _Guide]("http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete _Guide")

or


[http://ubuntuforums.org/showthread.p...20&mode=linear]("http://ubuntuforums.org/showthread.p...20&mode=linear")

should work no probs tho mate :)

---

### Post by iansl2000 on 2007-01-16
Thanks for the reply. before I follow the guides I have what seems to me to be a more fundamental problem.
When I go into  Terminal and type 

lspci

I get no response, only a return to the $ prompt.
Do I need to activate anything else before this will work?

I also have a Live CD of DSL (Damn small linux) which when I boot up and do 

lspci

in a Terminal I do get a list of devices including
 
RaLink:Unknown device 0301

I believe that this is the network card.
The DSL has a 2.4 Linux kernal if this helps

Ian

---

