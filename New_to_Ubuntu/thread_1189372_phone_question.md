---
title: "phone question"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by lozerfreek on 2009-06-16
i have a phone service thure medicom and would like to recive my calls on my computer i do not have a 56k modem and my modem has the phone built into it can i run the phone thure my mic and speakes or headset?

---

### Post by jonobr on 2009-06-16
Hello

And welcome to the forums,

Could you elaborate a bit on your setup?

You mentioned you dont have a 56k modem, but your modem has a phone built into it.

Could you elaborate more on that?

How do you connect to the Internet? IS it through a modem?

I would reckon the best way for getting this done is using an application like skype which uses voip and requires you to have a mic and a speakers /headset or you could use something like Ekiga on ubuntu and get a voip account for some application providers.

Most modems use their RJ11 ports to connect to a phoneline and allows you to dialup connect to an ISP.

The last analog modem development for modems was the v92 standard, (you see this on boxes when you buy modems.

These modems allow for faster connection on dialup as well as the ability to drop a data connection in favour of an incoming call .
Prior to V92 (as in v90 or V34) if you called a modem dialed into the Internet you got busy tone.

However, it did not go into the computer and allow you to use the pc to take the calls, it still required a physical phone to take that call.

Im not sure there is a technology that will do this, so again, I would consider using Skype or Ekiga....

---

### Post by lozerfreek on 2009-06-16
way over my head for now i guess. the modem is a internet modem and telephone modem in one :rca; dhg525  <-- make and model
i cant figure out skye or the ekiga to get them configured to accecpt my phone service

---

### Post by jonobr on 2009-06-16
Sorry about that, I did not meant to do that on purpose.

Looking at the make and model, you have a Cable modem, which means all the V protocols I mentioned are irrelevant to you.

I am going to look at this device over the next short while and see whats what.

Im getting the feeling you want to keep your telephone number?
If you setup Skype or Ekiga, you will have a new number, although some providors will allow you to bring you number with you.
Either way, I need to look at your cable modem first

Ciao

---

### Post by lavinog on 2009-06-16
> **lozerfreek said:**
> i have a phone service thure medicom and would like to recive my calls on my computer i do not have a 56k modem and my modem has the phone built into it can i run the phone thure my mic and speakes or headset?

not without a dial-up modem installed. The cable modem just provides the telephone jack just like a regular telephone company would.

You could get a phone with a headset port and plug that into your soundcard, but what would be the point?

---

### Post by jonobr on 2009-06-16
Looking at the dhg525 , it appears to have two telephone jacks which present RJ11 (regular telephone connections).

The manual describes it as a voip cable modem,

They obviously do the voice over IP in the box and IM not sure if they would let you at it and present the normal line to you.

I dont think you have a way of connecting that phone line to your pc and treat your pc as the phone, but Ill google around anjd see if there is anything interesting
I am thinking though- depending on the providor they may let you do voice over IP using your account from your computer.

Who is your providor?

Thanks

---

### Post by lavinog on 2009-06-16
> **jonobr said:**
> 
I dont think you have a way of connecting that phone line to your pc and treat your pc as the phone, but Ill google around anjd see if there is anything interesting
I am thinking though- depending on the providor they may let you do voice over IP using your account from your computer.

Most providers do not let you for security reasons. (some wardriver would find a way to make phone calls using your phone number.)

---

### Post by jonobr on 2009-06-16
Agreed with that, also, companies providing telephone service don't like doing voip unless they can implicitly control it,
ie having a device that does voip and give you the telephone line

---

### Post by lozerfreek on 2009-06-16
its thrue medicom

---

### Post by lozerfreek on 2009-06-16
boned

---

### Post by lozerfreek on 2009-06-17
<>

---

### Post by lavinog on 2009-06-17
Why do you want your phone to go through your computer anyway?
Why not use a phone?
If it is that important, you still can use a dialup modem.

---

### Post by lozerfreek on 2009-06-21
i want to be able to use my home phone on my laptop at work

---

### Post by lavinog on 2009-06-22
There are ways to use your laptop as a voip phone, but if you want to use your same phone number you are going to have to port it to a different service (ie cancel your phone number with medicom and use your laptop exclusively) or get a new number.
here is one way you can do it: [http://www.vonage.com/device.php?type=VPHONERB&refer_id=WEBPR0706010001W1&lid=product_title_VPORTAL](http://www.vonage.com/device.php?type=VPHONERB&refer_id=WEBPR0706010001W1&lid=product_title_VPORTAL) There are similar devices for other companies.

---

### Post by linuxpenguin on 2009-07-08
You are a little unclear as to what you're asking.  It sounded at first like you wanted to plug your computer speakers and microphone into the phone jack. . . now it sounds like you want to transmit your phone call audio through the Internet.

What do you mean by "use my home phone on my laptop at work"?  You mean, as in make and take calls from your home phone number while you're at work?  Or, you take your work laptop home and make and take phone calls from it?

I'm sure these are both do-able.  I'm not sure how you'd do the first one (and honestly, it sounds like a really bad idea - both because hackers might be able to tap your call, and because everyone else in the cube will get annoyed at you taking personal calls all day) but for the second one, you can use a voice modem.  I'm not sure what software you need (trying to find out myself :( ) but you can do it - in Windows I can use a program called Phoner.

Also - for the first one, some VoIP services can do this.  At my house we have Vonage, and if the power/Internet goes out then the calls get forwarded to a cell phone number.  There is also an option for us to pay extra to allow us to make and take calls from a laptop like you're describing - but it's not worth it IMO.

---

