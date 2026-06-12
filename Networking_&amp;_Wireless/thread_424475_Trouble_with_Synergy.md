---
title: "Trouble with Synergy"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by xfalconx2 on 2007-04-26
I am having some trouble getting Synergy to switch screens.  The server is my XP desktop (my main machine) and my client is Ubuntu Feisty 64-bit.  The client can connect just fine to the server and moving my mouse to the edge of the screen switches the mouse over.  However, it does not switch the screen; I'm still looking at my XP desktop with the mouse on the Ubuntu one.  I can get the mouse back onto XP by moving all the way to the right, and my log says the switches have been made.  Now, how do I get the screen to switch too?

One thing to note is that I am currently connecting the machines through a KVM switch.  I want to get Synergy working so that I can sell the KVM.  It works well, but I want the money.  Perhaps the KVM has something to do with this?  Surely not, though.

Thanks.

---

### Post by regal_dunce on 2007-04-26
If I understand you correctly, you're using one monitor with two inputs (XP and Feisty) and switching back and forth with synergy?  I guess you have to press the button on the monitor to switch, or does the KVM do that for you?

I use synergy daily to connect my laptop (running feisty) to my box at work (running red-hat enterprise).  One thing that I've noticed  is that when the screen on my laptop shuts off (I don't use a screensaver) then I can't use the mouse on my synergy server to bring the screen back to life.  The mouse is not on the server's display, it's somewhere under the screen on the client.  I have to manually move the mouse with the touchpad on the client, and then everything works fine.

Perhaps when you switch inputs on your monitor to your feisty box, it doesn't detect a signal, since the mouse won't bring the system back from standby.  I would try turning off any screen-savers or monitor shutoff functions in fiesty, and see if you can switch back and forth then.  

If everything I've said above is bogus, could you please post your synergy.conf file?

---

### Post by xfalconx2 on 2007-04-26
Ok, well, Feisty is not in standby.  I am actively working on both computers as I am trying to get Synergy to work.  I just unhooked the KVM and put the controls directly into the XP machine to see if that helped, but the mouse and keyboard still switch to Ubuntu but not the screen.  The synergy.conf file should not matter since XP is my server.  However, I have XP to the right of Ubuntu and Ubuntu to the left of XP.

Edit: I can set Feisty up as the server and connect to it with my XP box and it will do the same thing, switch the mouse and keyboard but not the screen.

Another edit:  I thought about it for a sec, and since you are trying to help me, I guess I should post what you asked for.  Here's my synergy,conf (I actually have my computers named with my real name, so I changed the computer names to match which OS it is):

    section: screens
       xp:
       ubuntu:
    end
    section: links
       xp:
           left = ubuntu
       ubuntu:
           right = xp
    end

---

### Post by regal_dunce on 2007-04-26
But I am right in assuming that you're using a single monitor with dual inputs?  In that case, I think you have to manually push the button to switch screens.  Here's a quote from the synergy website:

> 
Synergy lets you easily share a single mouse and keyboard between multiple computers with different operating systems, each with its own display, without special hardware. It's intended for users with multiple computers on their desk since each system uses its own monitor(s).


Perhaps it's time to buy a second monitor... dual display sure is nice ;)

---

### Post by xfalconx2 on 2007-04-26
Ah, I see what you were saying in the initial post then.  I am trying to use a single monitor for two computers.  The monitor only has one output, which is plugged into the KVM currently.  So is Synergy not meant for two computers with only one monitor to use between them?

---

### Post by regal_dunce on 2007-04-26
Yup, as far as I know, synergy just connects two computers with two separate monitors side by side.  Someone much better than me could probably hack synergy to have it send a switch signal to your KVM, but I wouldn't even know where to begin.  I guess that doesn't help you selling the KVM anyways.  

Good luck with your setup!

---

### Post by xfalconx2 on 2007-04-26
Thanks, though.  That is disappointing.  Too bad I misunderstood the purpose of the software because it got my hopes up.

---

### Post by eaughenbaugh on 2007-05-03
Actually synergy is a great tool. I use it on two windows machines. but what it does is allow a single keyboard and mouse to be shared on multiple computers. For example I have a workstation and a server, I have the keyboard and mouse on the workstation and synergy running. I have two monitors (one for each system) Picture the workstation monitor on the left and the server on the right. With synergy running and configured, when my mouse moves to the right of the workstation machines screen edge it moves to the server and my mouse and keyboard now function on the server move it to the left of of the server screen and it continues to move to the workstation monitor in which now the keyboard and mouse function again on the workstation. Synergy can actually have many systems and moniters... even above and below. So in technical terns it is a software KVM switch that works thru ethernet connection. I am currenty trying to get it to work with Ubuntu and windows XP. I have not had luck compiling it on Ubuntu yet :(

---

### Post by regal_dunce on 2007-05-04
> **eaughenbaugh said:**
> I am currenty trying to get it to work with Ubuntu and windows XP. I have not had luck compiling it on Ubuntu yet :(

Synergy's in the repo's man!  sudo apt-get install synergy and you're gravy!  It is a great tool, I agree, I use it every day too.

---

### Post by eaughenbaugh on 2007-05-04
> **regal_dunce said:**
> Synergy's in the repo's man!  sudo apt-get install synergy and you're gravy!  It is a great tool, I agree, I use it every day too.

Cool, I logged in from work and it install... can't wait to get home and test it. Thanks man!!!

---

