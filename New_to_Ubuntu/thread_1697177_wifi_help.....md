---
title: "wifi help...."
date: 2011-02-28
forum: New to Ubuntu
---

### Post by steffani on 2011-02-28
hi. i'm lost ......last night i accidently changed my whole computer to lucid lynx , because i wanted an updated gimp for my work.....it was a bad idea. my wifi is not working anymore and i really dont know enough about computers to understand what it wants.....
its asking me for a: SSID 
a: BSSID
a: MAC adress
and its not just disscopnected but there is an error says could not find info on interface "wlanO:avahi'in/proc/net/dev
so very very lost with this... im so thankful that these forums exsist :Dox steff
(oh p.s i am also being asked for my keyring password....and i type in the only password i have and it says that it is not correct....help!!!!) xo:confused:

---

### Post by steffani on 2011-02-28
any one out ther who can help me ?

---

### Post by Miub on 2011-02-28
Whats the problem

---

### Post by steffani on 2011-02-28
oh hi....sorry was waiting so long didnt think anyone was there......last night i did something really silly as i dont know anything about computers...and i ramdomly changed my hardy heron on dell to lucid lynx cause i wanted an updated gimp.....so the probelem are many but the most important one is that i can not get my wifi to work ....mostly because i do not know what it is asking for .....
it is saying that it could not find  info on interface..ect...please contact system administrator.....and it askes for the BSSID and MTU  and i really dont know ....ahhh help!:(

---

### Post by steffani on 2011-02-28
can anyone tell me why my computer is telling me that my password that i use to login is no longer  martches my "login keyring" I really dont know what that means and i think its kind of important seeing as i accidently changed my computer from hardy heron to lucid lynx last night....can anyone help....

---

### Post by steffani on 2011-02-28
im also having wifi connection problems......can anyone help......wow im even getting lost on these forums where i can;t seem to find my other threads......how am i such a dork? please help. not with the dork part but wifi hahahaha.....ha....ha....:confused:

---

### Post by overdrank on 2011-02-28
Hi and welcome, please do not create multiple threads on the same issue. It is polite on the forums to bump your thread once a 24 hr. Threads merged.

---

### Post by steffani on 2011-02-28
okay so instead of helping you just terll me off and thats suppose to be polite? im even more confused......thanks

---

### Post by steffani on 2011-02-28
> **Miub said:**
> Whats the problem
 are you still available to help?
:)

---

### Post by TechWiz2100 on 2011-02-28
Arguing with the mods is not a great way to start off at any forum just so you know.

Anyway, can you post the results of the following commands from terminal
```

lspci
cat /etc/network/interfaces
```

Since you upgraded to Lynx I assume you are having issues with older drivers. Try updating again to play catchup wit the repos and maybe compatible drivers will get installed.

---

### Post by steffani on 2011-02-28
> **TechWiz2100 said:**
> Arguing with the mods is not a great way to start off at any forum just so you know.
 
Anyway, can you post the results of the following commands from terminal
```

lspci
cat /etc/network/interfaces
```
 
Since you upgraded to Lynx I assume you are having issues with older drivers. Try updating again to play catchup wit the repos and maybe compatible drivers will get installed.
 hi thanks for helping...is that code one line and how is it that i can post the response if im working online from another computer to fix my computer that is not online .....

---

### Post by steffani on 2011-02-28
and if you could walk me through it all a bit slower...and in "im someone who knows nothing about computers I have ubuntu cause my ex put it on for me" launguage......that would be really super awesome.....:KS

---

### Post by TechWiz2100 on 2011-02-28
Applications > Accessories > Terminal and type in the commands as they are pressing enter for each new line. Then you can just drag to select text and drop it into a reply in either quotes tags or code tags (There are buttons in the editor for that as well)

If you need anything else don't hesitate to ask. We (by we I mean me lol) don't judge here on the Ubuntu forums

---

### Post by steffani on 2011-02-28
> **TechWiz2100 said:**
> Applications > Accessories > Terminal and type in the commands as they are pressing enter for each new line. Then you can just drag to select text and drop it into a reply in either quotes tags or code tags (There are buttons in the editor for that as well)
 
If you need anything else don't hesitate to ask. We (by we I mean me lol) don't judge here on the Ubuntu forums
hi so  actually all it tells me is no such file or directory.

---

### Post by TechWiz2100 on 2011-03-01
> **steffani said:**
> hi so  actually all it tells me is no such file or directory.

For which command(s)? I only listed standard tools that should all be available on any linux distro and /etc/network/interfaces is a file that is definitely in all Ubuntu editions

Did you check your spelling maybe?

---

