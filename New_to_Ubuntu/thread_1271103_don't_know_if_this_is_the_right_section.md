---
title: "don't know if this is the right section"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by cha0ticlol on 2009-09-20
alright my bro added a new router (we now have 2) but now my computers net connection sucks and i disconnect every 20seconds or something stupid, (i think the new 1 is intercepting the other because i unplugged the new 1 and my net worked fine) my bro insists to keep it in tho! it only disconnects for me but not any1 else in the house, i switched to ubuntu recently so i'm not sure how i would supply info but any help is appreciated ;x

---

### Post by mapes12 on 2009-09-20
Hi and welcome to the forum

You will need to give us much more specific information about the router configuration such as:

1. Why do you need 2?
2. How many machines are attached to them and which routers?
3. What OS these machines are using?
4. Do you use broadband or dial up?
5. Ethernet or wifi and which machines?

We can help but we need the LAN info first.

Best wishes.

Mark

---

### Post by cha0ticlol on 2009-09-20
> **mapes12 said:**
> Hi and welcome to the forum

You will need to give us much more specific information about the router configuration such as:

1. Why do you need 2?
2. How many machines are attached to them and which routers?
3. What OS these machines are using?
4. Do you use broadband or dial up?
5. Ethernet or wifi and which machines?

We can help but we need the LAN info first.

Best wishes.

Mark
hi mark, thanks.

I don't know why we need 2, my brother said it would 'boost' our strength.
there's usually 3 machines and an iphone connected & a belkin and sky 1 (maybe a modem?)
every machine is running windows xp except for mine which is runnin jaunty jackalope.
broadband
wifi on all of them

i don't know what LAN means sorry.

thanks again

crispy

---

### Post by Shazaam on 2009-09-20
LAN= Local Area Network (pc's behind a router/hub etc.)
WAN= Wide Area Network (usually the internet)
WLAN= Wireless LAN
[http://www.practicallynetworked.com/](http://www.practicallynetworked.com/)

---

### Post by halitech on 2009-09-20
all 2 routers will do is confuse things. are both routers connected to the internet modem? if so, how? Windows will generally connect to the last access point it connected to and stay connected but it seems in my experience, ubuntu will try to connect to whichever access point has the strongest signal. Are both routers using the same protocal? ie. wireless G or is the new one using a better connection? If the new router seems to have a stronger signal, then maybe you should only connect to that one and remove the old one.

---

### Post by cha0ticlol on 2009-09-20
sorry to confuse you all but theres not 2 routers, theres 1 router and a modem.
I'm not too sure about that though. theres the one where you plug the wire into (the grey 1) and a belkin one. the new (belkin) router is much stronger. Its nothing about connecting to any, either one i connect to i disconnect every time. sorry for the confusement :P

---

### Post by halitech on 2009-09-20
is the modem a combination modem/router? normally most modems can only give 1 connection at a time unless you are using a router unless it is a combination modem/router.

---

### Post by cha0ticlol on 2009-09-21
the new belkin router is connected to the sky modem/router if that helps

---

### Post by halitech on 2009-09-21
ok, what I would do in this situation, is remove the belkin for now, log into the sky modem/router and disable the wireless and DHCP function. Then connect the belkin and enable the wireless and DCHP (if not already enabled) so that only 1 device is giving out IP addresses so you don't get the cross-talk and disconnections.

---

### Post by cha0ticlol on 2009-09-21
can't do that cuz both are used, is there anyway i could block the new belkin router from my machine so theres no trouble at my end because it only applies to me

---

### Post by djyoung4 on 2009-09-21
did you try right clicking on the wireless network connection notification thing going to edit connections>wireless tab and just deleting the belkin network

---

### Post by gordintoronto on 2009-09-21
Is it possible both routers are on the same channel?  Try changing channels.

---

### Post by cha0ticlol on 2009-09-21
@djyoung
yep i tried that and i still have the same problem, thanks for your post anyways

@gordin how do i switch channels

---

### Post by djyoung4 on 2009-09-21
may i ask why your brother says you need two routers.  the belkin router is kind of unnecessary unless your brother knows exactly what he is doing with them.

---

### Post by desperado665 on 2009-09-21
By adding a second router, your brother has essentially created a "bridge". A bridge is only necessary when connecting two separate networks that consist of different protocols (such as TCP/IP with AppleTalk). So unless your brother uses a MAC or is using a protocol other than TCP/IP, the second router can do nothing other than cause headaches. As far as I am aware, you cannot "stack" routers for better signal strength.

---

### Post by cha0ticlol on 2009-09-22
thankyou! thats exactly what ive been saying to him, he doesnt listen. Whenever i get the chance i unplug the new belkin, but he always just plugs it back in.

---

### Post by GerMulvey on 2009-09-22
Desperado665 is right.
The only thing your brother can be thinking is using the routers to extend the wifi range. But if he's in the same house it's not gonna help.  Also if both are using dhcp then it will cause problems. You really only need the one router. Of course convincing your brother seems to be the problem. Hopefully you can make him see sense.

---

