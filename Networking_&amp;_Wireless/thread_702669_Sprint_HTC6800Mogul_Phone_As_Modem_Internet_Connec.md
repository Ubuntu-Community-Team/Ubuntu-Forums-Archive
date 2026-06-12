---
title: "Sprint HTC6800/Mogul Phone As Modem Internet Connection"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by trmentry on 2008-02-20
I have a Sprint Mogul (HTC PPC 6800).   I'm trying to get it to work as a modem in Gutsy.  I've read various posts on this but I'm not sure if its really this complicated.

When I plug the phone into a usb port on my laptop... the laptop makes an eth2 connection (0 = wired, 1= wireless).   It attempts to get an IP but fails.  

I go to my phone  Start --> Programs --> Internet Sharing

select PC Connection as USB
Network Connection as Phone As Modem.

It attempts to connect.  As it is attempted... the laptop sees this and tries to get an IP again.

The phone then errors out saying

```

Error 67: Registration Failure.  Your PCS Vision username/password maybe incorrect.

```

so digging a bit more  I found that there is a profile called 'Phone As Modem' in
Start --> Settings --> Connections Tab --> Connections --> Manage Exisiting Connections.

Under there is a Phone As Modem... I edit the settings and there is a section in there for username and password.

reading other posts.  I put my username as  [email]1112224444@sprintpcs.com[/email].  But I'm not sure what to put for the password.  I tried various combinations of sprint .. like sprint1 sprintpcs1, etc.  no joy.

Anyone have an idea what the password would be?  Do I need to call sprint to get phone setup more?  My plan with the Mogul has unlimited data on the plan that I'm on so figure that I don't need to pay for additional addons.

thanks

---

### Post by trmentry on 2008-02-20
I was reading the Sprint document on their site about Linux and the broadband cards.

[http://tinyurl.com/8bjua](http://tinyurl.com/8bjua)  (select linux)

it saying that the device has to be activated/registered with a windows machine first.  

Guess I need to find a windows machine I can beat on to try this out.  

Anyone else had any luck?

---

### Post by anmghstnet on 2008-04-07
I don't know if you are still looking into this, but I do have something that may help you.

First of all, if you haven't already you should update the firmware for your phone. The newest version of the firmware does wonders.

As for the error 67, try the following:
start menu
phone
menu
options
services
internet
get settings
click on the start button.

This will reprovision your phone. Also, you should open internet explorer and browse to a site that requires the phone to connect to the internet before starting the internet sharing app.

Good luck!

---

### Post by ar1stotle on 2008-05-06
In case you didn't fix the error you were getting, I just figured that one out. You need to run a registry editor on the Mogul, go to HKLM-->Conn-->InternetSharing and delete the key Extension. That'll fix the error. I'm hoping I'll be able to connect through Ubuntu... only been able to connect through XP so far (that is, I haven't tried Ubuntu yet because I had to unplug that HDD).

---

