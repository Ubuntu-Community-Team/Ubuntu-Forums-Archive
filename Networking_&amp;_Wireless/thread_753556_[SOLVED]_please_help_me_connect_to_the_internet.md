---
title: "[SOLVED] please help me connect to the internet"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by rolledthatho on 2008-04-12
my computer crashed i reloaded windows XP and i dont have the disk/driver for my wirless card, but i looked up the model and went and downloaded it from the website its a GN-WP01GS so i downloaded it from here [http://www.gigabyte.com.tw/Support/C...?ProductID=970](http://www.gigabyte.com.tw/Support/C...?ProductID=970)

now that i installed it the wireless card icon in the icon tray no longer has a red X over it and its green and running, also the red X over the two little icon computers (network) went away and it popped up saying signal strength very good, 54 MB or whatever, yet NOTHING when i click on a webpage it immediatly says connect or work offline

and yes i understand this is ubuntu forums so dont flame too hard, but there are many people on these forums who have helped me before, and the knowledge here is endless. thanks for any help

---

### Post by superprash2003 on 2008-04-12
please go to the terminal and type ifconfig and post results here

---

### Post by rolledthatho on 2008-04-12
hey man im guessin you didnt finish reading my post, haha its my fault either way trying to find windows help on an ubuntu forums, but yeah. im here for the knowledge of computers thats on this forum, but yeah im running windows :)

if you can still help im def down for some imput!

thanks

---

### Post by superprash2003 on 2008-04-13
oops.. sorry about that.. i actually wanted to know whether you are successfully getting an  ip on your machine or not.. i am so used to saying ifconfig i just forgot abt your setup..sorry.. please go to command prompt (Start->run and type cmd) .. and then type ipconfig and post results here also type ping google.com and post results here

---

### Post by rolledthatho on 2008-04-13
ethernet adapterwireless connection networks

connection specific DNS suffix... :
ip address...........................: 192.168.0.1
subnet mask........................: 255.255.255.0
default gateway...................:

also the results for the ping google.com were: ping request could not find host google.com please check the name and try again

and thanks again for all your help!

---

### Post by superprash2003 on 2008-04-13
you seem to be getting a wrong ip or you have entered it wrongly.. 192.168.0.1 cannot be set as ip , and also the gateway hasnt been specified.Go to control panel->Network Connections->Right click on the wireless adapter..click on properties.there you will find tcp/ip propterties .. click on that.. and change to Automatically assign ip (or something like that).. try that way.. and try ping google.com and try surfing..
  if that does not work.. tell me the ip of your router.

---

### Post by rolledthatho on 2008-04-13
bout to do that now, if your online stay posted.

---

### Post by rolledthatho on 2008-04-13
THANK YOU SOOOOOOOO much, for everyone else, please note this as solved and by the directions super gave above..

thank you, thank you, thank you!

---

