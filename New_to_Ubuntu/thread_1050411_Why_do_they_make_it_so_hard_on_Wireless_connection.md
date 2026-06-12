---
title: "Why do they make it so hard on Wireless connections?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Copitox on 2009-01-25
I'm not an absolute beginner, but i'm asking this in place of my dad.

I'll explain the title. In Windows you choose the Wireless Connection and enter the password. In Ubuntu you ALSO have to select what type of password does the connection have. ¿What's the point? that just confuses beginners and make you waste time when you don't know that. ¿Is there a way to configure it as an automatic detection like in windows?

Thanks

---

### Post by pi.boy.travis on 2009-01-25
Once you connect to the network successfully, Ubuntu 8.10 should automatically connect to it whenever you are in range.

---

### Post by sleepyjon on 2009-01-25
> **pi.boy.travis said:**
> Once you connect to the network successfully, Ubuntu 8.10 should automatically connect to it whenever you are in range.

I think the OP is talking about the password type, not connecting itself.

WICD does detect the encryption type: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I don't know about NM, I haven't used it for a long time.

---

### Post by Copitox on 2009-01-25
I know WICD tells you what the encryption type is, but you still have to choose it.. and is not only choosing between WEP and WPA, there are like four types of encryption types.. what i want is to just put the password, so my dad won't bother with things he doesn't care about!

---

### Post by sizzlefire on 2009-01-25
Why don't you just make the computer automatically connect to the network? That way, he wouldn't even have to put the key. If all else fails, you could always try a different network connection manager.

---

### Post by llamabr on 2009-01-25
No one else seems to understand your question.  Sorry.

I think there are two good answers.
First, Linux is infinitely configurable, and most users like the OS for that reason.  People who want a shiny START button generally don't want linux.  
Next, I'm not a huge user of Network Manager, but I believe that, even if it gives you the option, it will connect using the correct encryption type, even if you chose the wrong one.  It uses that information to know when to ungrey the 'connect' button.  And I also think you can just skip answering that box altogether.

FWIW, my mac osx also asks if I'm using WEP or WPA.

---

### Post by Copitox on 2009-01-25
I know i can do that, but lets suppose he goes somewhere else... an hotel! and he wants to connect. Should a user who just listens to music, check the weather and use openoffice know how to recognize the difference between:

WPA 1/2 (Passphrase)
WPA 1/2 (Preshared key)
WEP (Hex)
WEP (Passphrase)
WEP(Shared-Restricted)
LEAP with WEP
TTLS with WEP
EAP-FAST
PEAP with GTC
PEAP with TKIP
EAP-TLS

there's no need! he should just select a network, enter the password and that's it!
there's no need complicating an unexperienced user with that stuff!

@llamabr: as you said, macosx ask you between WEP and WPA, not all that stuff i listed before! Besides, WICD won't connect until you choose the right encryption type.


PS:I dont hate linux because of things like this. I'm just saying that linux is not as ready for the common user as it claims.
PS2: I love linux, i'm not attacking it, i just want to figure out why do developers keep it hard
PS2:sorry my bad english, i'm from southamerica.

---

### Post by garwaymatt on 2009-01-25
Maybe this should be raised with the Gnome usability people? If the type of encryption can be detected from the one typed in. I suspect that you may need to select WEP/WPA though.

---

### Post by perce on 2009-01-25
You don't have to choose: Network Manager will choose one for you (the first you see in the list). The menu is there only if Network Manager makes the wrong choice for whatever reason (something that may happen, but not very often).

---

### Post by garwaymatt on 2009-01-25
My misunderstanding, The only wifi I have used under 8.10 are open access points.

---

### Post by Copitox on 2009-01-25
Does WICD have an auto encryption type detection option or something?

---

### Post by Kareeser on 2009-01-25
I believe it does. nm has always detected the correct encryption for any protected network I've thrown its way.

Perhaps a better idea for the usability people would be to ensconce the password type drop-down box in a hidden area of its own... "Advanced", perhaps?

---

### Post by imdano on 2009-01-26
> **Copitox said:**
> Does WICD have an auto encryption type detection option or something?No we don't.  I think the template system we use for encryption now is one of the weakest parts of the whole program, and we're planning to rewrite the entire system fairly soon.  Right now it forces you to create a completely new template for every configuration tweak, which makes for a long and cluttered list of encryption types to choose from.

It is possible autodetect what type of encryption to use to a certain degree, but there are still some crappy drivers out there that do not give you all the information you need.  And even if you do know what type of encryption is in use you don't necessarily know all the credentials the user needs to supply to connect.  Windows has to deal with the same issues, and something like EAP-TLS is in use the user has to go through some advanced menus to set everything up correctly.  Windows just does a better job of hiding that stuff for users who just use standard WPA or WEP (which is most people).

---

### Post by timcredible on 2009-01-26
why not remove the password on the wireless router and then it's the same, just click on the ssid.  if you're concerned about security, use MAC filtering on the router.

---

