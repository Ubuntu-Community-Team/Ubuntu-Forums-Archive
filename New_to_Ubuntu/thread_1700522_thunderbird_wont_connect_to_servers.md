---
title: "thunderbird wont connect to servers"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by jimbean on 2011-03-05
i called my email provider and he gave me port settings and made sure everything was configured correctly
but after latest upgrade of ubuntu i cant get any email client to work
firefox works update manager works hardware drivers installation works

---

### Post by runeh76 on 2011-03-05
Hi

Are u using mobloguer or firewall?

---

### Post by jimbean on 2011-03-05
i checked firewall and it came back disabled dont know what other thing you said is

---

### Post by runeh76 on 2011-03-05
Never mind about Mobloguer, u would know if u use it.
hmm whats email? hotmail, gmail?? Double check ur settings.

---

### Post by jimbean on 2011-03-05
more than 20 times checked settings
just a local dsl service provider is my email client

---

### Post by runeh76 on 2011-03-05
Oh okey, then i dont know..maybe ISP have problems?
If u havent touch ur iptables rules and u dont have firewall or else what could block ur email..
Do u have router?

---

### Post by jimbean on 2011-03-05
i upgraded thunderbird from synaptic and removed evolution 
still no go

---

### Post by jimbean on 2011-03-05
just dsl modem  direct connection

---

### Post by runeh76 on 2011-03-05
I remember something that, when i removed evolution..there was some dependencies... Try to install it back.

---

### Post by jimbean on 2011-03-05
reinstalled evolution
ran thunderbird
connection to pop server timed out

---

### Post by runeh76 on 2011-03-05
Try to configure evolution and try that?
also u can ping ur email server, if that success, ur email-settings are wrong.

---

### Post by jimbean on 2011-03-05
pop.*****.net wont ping

---

### Post by jimbean on 2011-03-05
[www.pop.*****.net](www.pop.*****.net) wont ping

---

### Post by jimbean on 2011-03-05
[www.*****.net](www.*****.net) wont ping
[www.yahoo.com](www.yahoo.com) will ping

---

### Post by runeh76 on 2011-03-05
U see? Now u can login ur email straight with browser, so u can see if server is working. 
I believe that u have checked ur settings, but maybe they gave wrong settings..?  :)

---

### Post by runeh76 on 2011-03-05
Have u seen this?:

[http://ubuntuforums.org/showthread.php?t=1386461]("http://ubuntuforums.org/showthread.php?t=1386461")

---

### Post by jimbean on 2011-03-05
dont see
what do you mean still no email
from desktop
i can type server address in address bar in firefox and go to there site
but i cannot recieve email through thunderbird or evolution

---

### Post by runeh76 on 2011-03-05
I mean that ur settings are wrong. pls check that earlier link.

---

### Post by jimbean on 2011-03-05
my isp is vague 
does anybody know {squirrel mail} translation into webmail extensions
which extension ???

---

### Post by runeh76 on 2011-03-05
Forget about ur ISP  :)
Just create new email, example Gmail.
It works "out of the box"  ;)

Good luck!

---

### Post by jimbean on 2011-03-05
im guessing but my isp is powered by google
so im trying to install the gmail exstension and this is what it says

WebMail - GMail 0.6.6 could not be installed because it is not compatible with Firefox 3.6.13.

---

### Post by jimbean on 2011-03-05
web mail wont download either

WebMail 1.3.11 could not be installed because it is not compatible with Firefox 3.6.13

---

### Post by jimbean on 2011-03-06
ok this is something that makes me curious my wired connection in network settings is being used
but my dsl connection with screen name and password is not being used
ive tried to set up name and password in the wired security settings but it wont let me apply setting
the dsl has name and password set but my computer wont use the dsl connection ive set it manually and automatic

---

### Post by jimbean on 2011-04-03
ok i got email don`t know exactly what i did but i am writing this down for further investigation for myself
1st i went to my isp and looked over all settings changed pop3 to pop
in user settings changed port settings for incoming and outgoing mail
still did not work
2nd i went to this site, [https://help.ubuntu.com/8.04/serverg.../firewall.html](https://help.ubuntu.com/8.04/serverg.../firewall.html)
and did second line in terminal thing in there instructions
did not work
3rd i did the 5 th line in terminal and started recieving email

ive tried to disable ufw before and it did not work for sending and recieving email
and i also removed ufw from 10.10 maverick meerkat and it almost hosed the whole system
not solved yet still testing over next week

---

