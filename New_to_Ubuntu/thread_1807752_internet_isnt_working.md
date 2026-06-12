---
title: "internet isnt working"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by :Doppler: on 2011-07-19
Hi!
i just downloaded Natty 11.04 but i didnt use a live cd i just dowloaded it from the ubuntu site and ran it side by side with windows. is that why my internet isnt working? i am currently using my desktop and  natty is on my lappy. can you help? my network controller is a broadcom corp bcm4311 and is compatible and if i try and enter the ndiswraper into the gnome it says it isnt installed and when i try to install it it wont let me input my pass into the terminal.

thank you for you help!

---

### Post by ikt on 2011-07-19
> **:Doppler: said:**
> my network controller is a broadcom corp bcm4311 and is compatible and if i try and enter the ndiswraper into the gnome it says it isnt installed and when i try to install it it wont let me input my pass into the terminal.

thank you for you help!

If you aren't connected to the internet it will be unable to download ndiswrapper, do you see anything in regards to a wireless driver in the 'additional drivers' program?

---

### Post by Jguy on 2011-07-19
> **:Doppler: said:**
> Hi!
i just downloaded Natty 11.04 but i didnt use a live cd i just dowloaded it from the ubuntu site and ran it side by side with windows. is that why my internet isnt working? i am currently using my desktop and  natty is on my lappy. can you help? my network controller is a broadcom corp bcm4311 and is compatible and if i try and enter the ndiswraper into the gnome it says it isnt installed and when i try to install it it wont let me input my pass into the terminal.

thank you for you help!

When you say 'it won't let you input your password into the terminal', are you describing getting to the 'Enter Password:' prompt and then not seeing anything as you type? That's intentional. You won't see anything. This is to prevent people from seeing how long your password is by looking over your shoulder.

---

### Post by jfbooth on 2011-07-19
> **:Doppler: said:**
> Hi!
i just downloaded Natty 11.04 but i didnt use a live cd i just dowloaded it from the ubuntu site and ran it side by side with windows.

I am no linux expert, but want to ask you .. from the above, seems you used the WUBI installation .. right????

If so .. I THINK it uses a wrapper whereby it uses your WINDOWS code to connect.  When I have installed WUBI in the past .. to a Windows machine that is working wirelessly, the Wubi install worked with no configuring on my part.

Soo, I did not answer your question .. at all .. but basically wanted to clarify if you installed via WUBI.

---

### Post by :Doppler: on 2011-07-19
i clicked on additional drivers and i was given a prompt saying downloading package indexes failed plaease check your network status. most drivers will not be available.

---

### Post by :Doppler: on 2011-07-19
yeah! i did the WUBI install

---

### Post by jfbooth on 2011-07-19
> **:Doppler: said:**
> yeah! i did the WUBI install

You might want to connect your lappy to your modem/router via Ethernet cable (if now wireless) and see if UBUNTU gets on the 'net that way (for the heck of it).

---

### Post by :Doppler: on 2011-07-19
ok so i connected an ethernet and im on my lappy now is there anyway i can make the connection wireless? does any one need anthing from gnome to help the trouble shooting? 


should i try download the ndiswrapper now?

---

### Post by amjjawad on 2011-07-19
> **:Doppler: said:**
> Hi!
i just downloaded Natty 11.04 but i didnt use a live cd i just dowloaded it from the ubuntu site and ran it side by side with windows. is that why my internet isnt working? i am currently using my desktop and  natty is on my lappy. can you help? my network controller is a broadcom corp bcm4311 and is compatible and if i try and enter the ndiswraper into the gnome it says it isnt installed and when i try to install it it wont let me input my pass into the terminal.

thank you for you help!

Hello and Welcome :)

Long story short, the LiveCD has a great advantage that you'll need in your case.
LiveCD is very helpful because "before" you install Ubuntu, you can check whether it will work well with ALL your hardware. NO OS is perfect. Some hardware drivers will not work out-of-the box.
Thus, LiveCD is needed.

For me, if you ask me, I don't prefer Wubi installation. I have some good reason for that. I prefer LiveCD, Installation on USB/External HDD for learning purposes. I do prefer HDD Installation for long run usage.

Good luck!

---

### Post by :Doppler: on 2011-07-19
so the driver just updated for my network adapter but wireless wtill isnt working im newb and dont know how to use the wireless conection thing in natty -_-

---

### Post by jfbooth on 2011-07-19
> **:Doppler: said:**
> so the driver just updated for my network adapter but wireless wtill isnt working im newb and dont know how to use the wireless conection thing in natty -_-

First, I have to tell you, I am "about" as new as you are.  Well, not really, but I am still learning.

I have used Wubi for a couple of Ubuntu releases.  One on an XP machine and another on a W7-64 machine.  I have NEITHER right now so have to help you from memory.

Like I said, I THINK Wubi uses your Windows drivers since Wubi installs Ubuntu INSIDE of Windows.  If Windows was working WIRELESS, Wubi install SHOULD work wireless.  If it doesn't, I do not have an answer for you unless it would be that Wubi Ubuntu is somehow not compatible with your lappy hardware .. but I would not conclude that just yet.  I suggested the ETHERNET connection simply to (temporarily) get you on the Net for trouble shooting.

If I were you, I would shut down, disconnect Ethernet cable, and boot up Ubuntu again and see if it NOW connects wirelessly.  If not, I really can't help you.

I want to tell you a little about Wubi.  It is great .. but it HAS LIMITATIONS.  One of them is you cannot change the desktop Unity to some other desktop should you wish to.  There are other limitations to a WUBI install.

If you would decide to burn your own live CD, you have much more flexibility.  1.  You can boot Ubuntu from it and 'test' Ubuntu BEFORE INSTALLING.  2.  You can DUAL BOOT Windows/Ubuntu.  3.  You can use your entire HD for Ubuntu.

If you elect 1. or 2. .. you will probably want to UNINSTALL Wubi from your Windows first.

If you try 1, 2, or 3 .. START OUT with your lappy connected ETHERNET.  Then it is on the NET to get updates and whatever you may need for WIRELESS.

I am sorry I cannot tell you what to do about a WUBI install not connecting wirelessly .. because I have never had the problem.

EDIT:  Does this laptop have a WIFI on/off button/key????

---

### Post by :Doppler: on 2011-07-20
thank you very much fo your support and input.

yes my lappy has a WLAN switch in the front of it my lappy madel is a HP pavillion dv6000 if that helps any.

---

### Post by :Doppler: on 2011-07-20
so when you say:

> **jfbooth said:**
> 
I want to tell you a little about Wubi.  It is great .. but it HAS LIMITATIONS.  One of them is you cannot change the desktop Unity to some other desktop should you wish to.  There are other limitations to a WUBI install.

  
does that mean i wont be able to use something like compizconfigsettings manager?

---

### Post by jfbooth on 2011-07-20
I feel that at this point, your biggest problem is ME .. because I am such a beginner with Ubuntu, myself.

> has a WLAN switch in the front of it

I THINK that might have something to do with it.  Remember, I said I have tried WUBI on two Windows machines and did not have to do anything to get them wireless?  Neither one of them had a switch.  It COULD be that Wubi Ubuntu needs something to 'handle' that hardware ... but I cannot say for sure.  There is a wireless networking section of this forum where you might get more qualified support.  Be sure to mention it is a WUBI install.

> does that mean i wont be able to use something like compizconfigsettings manager?

I have no idea.  The nice thing about Wubi is you can break it all you want .. simply UNinstall it from Windows (Add/Remove programs) and reinstall as often as you wish.  It is a pretty good 'learn it' environment.  To answer this question ... leave it connected Ethernet and go ahead and try to install whatever you feel like trying.  That would be my suggestion.

EDIT:  Here is a link to the network/wireless forum:  [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by wildmanne39 on 2011-07-21
Hi, I have that exact system and here is a link to get the card working, but I do not know if it will work since it is a wubi install but you can try and you do not need ndiswrapper and if you installed it remove it before installing the drivers for your card. 
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

If you need more help post back here and if it works mark thread solved.
Thank you

---

