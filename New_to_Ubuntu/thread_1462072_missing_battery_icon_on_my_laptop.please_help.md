---
title: "missing battery icon on my laptop.please help"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by human75 on 2010-04-25
hi there.
i just installed ubuntu 10 rc2 to my toshiba satellite a210 laptop.my battery icon is missing.i also notice when i plug my laptop charger there is no icon or notification appear.sorry i am very noob:)i tried couple of things to make it work i couldn't fix it.could you please help to fix?what should i do?thanks in advance..
ps:i installed ubuntu in multi boot mode.i dont know what is wrong but after ubuntu boot,in 3 minutes maybe less than that, my laptop turns off???looks like ubuntu can recognise the power setting?it acts like empty battery.
please help i really enjoy ubuntu.i am really sick and tired windows.i dont want to turn windows os bak.
thanks in advance..

---

### Post by Jon Monreal on 2010-04-25
The battery icon doesn't appear when the power cable is plugged in.

To fix this, go to the toolbar at the top and go to System -> Preferences -> Power Management. When the new window pops up, you will notice three tabs toward the top of the window; click on "General".

Below you will see a section titled **Notification Area**. Select "Always display an icon" under this, and you'll be all set.

If this solves your problem, please make sure to [mark this thread as solved]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6") by going to "Thread Tools" right above your first post there and selecting "Mark this thread as solved." Thanks.

---

### Post by blueghoti on 2010-04-25
Hi Jon - 

I too had a similar problem and followed your advice, but the problem remains.  Wondering if you have other ideas?

I'm running a (2 year old) Dell Inspiron 1520 with the original battery.  Until last week I was on Vista, but have since reinstalled the entire system with Ubuntu 9.10. 

A few weeks ago, I noted some power issues.  My power cord is fraying (!) and needs to be replaced.  Also the "low battery" light is always on when I unplug AC power - even though it still has a full charge and could last another hour.

I noticed both in Vista, and in Ubuntu (and the BIOS config, I believe) the system is reporting no battery.

I was hoping that Ubuntu might be able to recognise it anyhow - any thoughts?

Chris

---

### Post by aloprot on 2010-04-25
blueghoti, sounds like you need a new battery. Over time the battery life decreases, it's a normal thing. I'm no expert but this is what I think. Good luck!

---

### Post by Jon Monreal on 2010-04-25
> **blueghoti said:**
> ... My power cord is fraying (!) and needs to be replaced.  Also the "low battery" light is always on when I unplug AC power - even though it still has a full charge and could last another hour.

I noticed both in Vista, and in Ubuntu (and the BIOS config, I believe) the system is reporting no battery. ...

Your power cord fraying is a serious issue, and could possibly do damage to your system (or result in electric shock if you touch it). Electric tape and other repairs are not feasible solutions, so you should replace it ASAP.

The other issues could be with the BIOS, hardware, or the battery itself, and there's nothing you can do in Windows or Ubuntu to fix them. You could try replacing the BIOS (usually requires Windows to be installed) but there's no guarantee that will work either, as it could be a hardware problem.

---

### Post by daniell59 on 2010-04-25
> **Jon Monreal said:**
> The battery icon doesn't appear when the power cable is plugged in.

To fix this, go to the toolbar at the top and go to System -> Preferences -> Power Management. When the new window pops up, you will notice three tabs toward the top of the window; click on "General".

Below you will see a section titled **Notification Area**. Select "Always display an icon" under this, and you'll be all set.

If this solves your problem, please make sure to [mark this thread as solved]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6") by going to "Thread Tools" right above your first post there and selecting "Mark this thread as solved." Thanks.

Thanks, it worked for me. I just accepted the problem until I happened to notice the thread.

---

### Post by blueghoti on 2010-04-25
Thanks guys.  Yeah - I think I need a new power cord, HD and battery.  :-(  There's still life left in this laptop, otherwise I'd just replace the whole thing.

(Curiously, I actually think that it's because of poor recommended updates list from Dell that my problems started with Vista about a week ago.  Either that or really striking coincidence).

C

---

### Post by Jon Monreal on 2010-04-25
> **blueghoti said:**
> There's still life left in this laptop, otherwise I'd just replace the whole thing.

What are the specs, and how much will it cost to replace the components (are you replacing them yourself, etc)? There might be a sound financial argument for simply getting a new laptop.

---

### Post by human75 on 2010-04-25
> **Jon Monreal said:**
> The battery icon doesn't appear when the power cable is plugged in.
 
To fix this, go to the toolbar at the top and go to System -> Preferences -> Power Management. When the new window pops up, you will notice three tabs toward the top of the window; click on "General".
 
Below you will see a section titled **Notification Area**. Select "Always display an icon" under this, and you'll be all set.
 
If this solves your problem, please make sure to [mark this thread as solved]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6") by going to "Thread Tools" right above your first post there and selecting "Mark this thread as solved." Thanks.
   
    nop it didnt solve my problem mate.i am thinking my problem is not just a simple notification problem.looks like i am having ACPI problem or what:((
   first of all i do not have 3 tab i have just 2 tab on AC power and Genaral.yes i did "Always display an icon" but it just show thunder and it does not show battery level anyway...i am removing charger nothing i changing it just thunder?!!so thanks for your tip but it didnt work.
  another things i would like to ask why my laptop shuts off?because of overheating?so how could i understand what really problem is my friend.please help.i searched on google i found couple of thread abouth toshiba sattelite a210 topic.but i couldnt find answer.do you thing must i full install UBUNTU rather than WUBI?does it cause this problem?
  Many thanks in advance

---

### Post by blueghoti on 2010-04-26
> **Jon Monreal said:**
> What are the specs, and how much will it cost to replace the components (are you replacing them yourself, etc)? There might be a sound financial argument for simply getting a new laptop.

Hey Jon...  Yeah...  The time may come to do a bit of shopping :-)

---

### Post by Jon Monreal on 2010-04-26
> **human75 said:**
> nop it didnt solve my problem mate.i am thinking my problem is not just a simple notification problem.looks like i am having ACPI problem or what:((
   first of all i do not have 3 tab i have just 2 tab on AC power and Genaral.yes i did "Always display an icon" but it just show thunder and it does not show battery level anyway...i am removing charger nothing i changing it just thunder?!!so thanks for your tip but it didnt work.
  another things i would like to ask why my laptop shuts off?because of overheating?so how could i understand what really problem is my friend.please help.i searched on google i found couple of thread abouth toshiba sattelite a210 topic.but i couldnt find answer.do you thing must i full install UBUNTU rather than WUBI?does it cause this problem?
  Many thanks in advance

Yeah, that's not a notification problem. Let's try to diagnose and fix the turning off problem first, however, as that is worse from a usability standpoint.

Well, good news and bad news all-in-one: [you don't seem to be alone]("http://ubuntuforums.org/cat%20/proc/acpi/thermal_zone/THM/temperature"). To be sure that it's an overheating problem, try typing
cat /proc/acpi/thermal_zone/THM/temperaturebefore it shuts down, and post the output temperature here.

Also, can you hear the fan on your laptop running at any point? Does it sound stressed? If you hear nothing, try taking a look and seeing if the fan is stopped (or slowed down).

We can work from there to see if the problem can be fixed.

> Hey Jon...  Yeah...  The time may come to do a bit of shopping :smile:

If you live in the US, you might want to take a look at [system76]("http://www.system76.com/") as they offer systems with Ubuntu preinstalled.

---

### Post by human75 on 2010-04-26
> **Jon Monreal said:**
> Yeah, that's not a notification problem. Let's try to diagnose and fix the turning off problem first, however, as that is worse from a usability standpoint.

Well, good news and bad news all-in-one: [you don't seem to be alone]("http://ubuntuforums.org/cat%20/proc/acpi/thermal_zone/THM/temperature"). To be sure that it's an overheating problem, try typing
cat /proc/acpi/thermal_zone/THM/temperaturebefore it shuts down, and post the output temperature here.

Also, can you hear the fan on your laptop running at any point? Does it sound stressed? If you hear nothing, try taking a look and seeing if the fan is stopped (or slowed down).

We can work from there to see if the problem can be fixed.



If you live in the US, you might want to take a look at [system76]("http://www.system76.com/") as they offer systems with Ubuntu preinstalled.
i install kubuntu 10.04 X64 version battery and acpi starts work but this time my motorola s9HD headphone and my htc pda bluetooth didnt work:( what is wrong guys?why everything is unstable.am i doing something wrong?how can i fix this problems i really like kubuntu as well but it is not stable for my daily usage.please advice.what should i do.thanks in advance

---

### Post by Jon Monreal on 2010-04-26
> **human75 said:**
> i install kubuntu 10.04 X64 version battery and acpi starts work but this time my motorola s9HD headphone and my htc pda bluetooth didnt work:( what is wrong guys?why everything is unstable.am i doing something wrong?how can i fix this problems i really like kubuntu as well but it is not stable for my daily usage.please advice.what should i do.thanks in advance

Have you tried 9.10? If it works, you could always wait for updates to 10.04 and check if it works using a Live CD or Live USB.

---

