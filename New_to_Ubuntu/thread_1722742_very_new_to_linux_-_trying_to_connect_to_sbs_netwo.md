---
title: "very new to linux - trying to connect to sbs network"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by lucasfreight on 2011-04-06
Hi

I am totally fed up with ms windows on my local pc's and am currently trialling ubuntu 10.10

Our server is SBS2003 which to be fair, runs fine with no issues, touch wood and i would like to leave this alone but connect the users as ubuntu to the data on SBS and if possible the exchange for mail.

I have tried to look through your site and have seen something mentioning samba and windows share in the howtos but couldn't find anything that relates.

My question is... i assume i need to connect ubuntu on to the sbs network? how do i do this? once on the network then i will obviously be able to see the data.. first part done, how do i then connect the exchange up and which is the best software for mail and exchange connection.

If i can get this up and running i will be a happy chappie as my next problem is ms access to mysql... oh the joys :-)

looking forward to direction on where i can find more information on this and/or advice.

many thanks in advance
Adam

---

### Post by Paddy Landau on 2011-04-06
Welcome to Ubuntu.

Samba is a way of making Ubuntu access the LAN as if it were Windows, so Ubuntu can see Windows and vice-versa.

In theory, it's really easy. Once you have installed Ubuntu, you install Samba. Go to Ubuntu Software Centre (from the menu), and install [samba]("apt:samba"), [nautilus-samba]("apt:nautilus-samba") and [system-config-samba]("apt:system-config-samba").

Then, go to System > Administration > Samba and set it up. You can add your own shared folders to the network.

Reboot. (Theoretically, you shouldn't have to, but I often find I need to.)

Go to Places > Network, and you should find your folders.

Sometimes, it doesn't work first time; there can be teething problems. If it doesn't work, simply post your problem and let us help you. There's always a way around.

---

### Post by lucasfreight on 2011-04-06
Hi Paddy

Many thanks for your very speedy reply!! 

I want to find the SBS server on the Ubuntu machine but cant find it, any suggestions?

Thanks
Adam

---

### Post by lucasfreight on 2011-04-06
i see some information in the help about X Window System??

sorry -  i am really new to all this :-(

---

### Post by Paddy Landau on 2011-04-06
Sorry, I don't know SBS. It's Windows, isn't it?

Have you followed the instructions? Did you get any error messages? What happens when you go to Places > Network?

You need to be explicit, because we cannot see your machine from here.

---

### Post by lucasfreight on 2011-04-06
Thank you, i fully appreciate you cant and your help is VERY much appreciated!

I go to the network and can see "Windows Network" double click on it and it says opening and that i can click cancel to stop - doesnt do anything and then shows the error, unable to mount location - DBus error org.freedesktop.DBus.Error.InvalidArgs: mountpoint Already registered

i then leave that whilst i type this and another window popped up, the folder contents could not be displayed -

---

### Post by lucasfreight on 2011-04-06
WOO HOO!!! more playing and got the server data!!!

THANK YOU VERYU MUCH!!!

i'll be back - bit more learning to do! ;-)

---

### Post by Paddy Landau on 2011-04-06
Well done, I'm glad you found your solution.

Post again if you get further problems.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

