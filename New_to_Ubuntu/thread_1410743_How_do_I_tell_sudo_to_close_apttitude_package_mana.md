---
title: "How do I tell sudo to close apttitude package manager"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-02-19
I tried to install a program with sudo aptitude install and it worked but it got stuck for 15 mins trying to download a file so I just closed the terminal. I have had problems all afternoon with downloads to update my software packages. They have been getting stuck on downloading even tho my internet is working fine to use the browser. Anyway I need to shut down the apt process in the terminal. Can someone tell me how to do that pls :)

---

### Post by nothingspecial on 2010-02-19
Try ```
sudo apt-get install -f
```

---

### Post by ThePinkWitch on 2010-02-19
> **nothingspecial said:**
> Try ```
sudo apt-get install -f
```

I tried that using both apt-get and aptitude but it says it was unable to lock.  Uh oh  :(

---

### Post by nothingspecial on 2010-02-19
Do you have synaptic, software center or update manager open?

---

### Post by ThePinkWitch on 2010-02-19
> **nothingspecial said:**
> Do you have synaptic, software center or update manager open?

Thanks for your reply. I don't have either open. I shut down the terminal in the middle of downloading and installing a program. It's having a hissy fit :)

---

### Post by nothingspecial on 2010-02-19
Do you have an exact error message?

---

### Post by Troll_the_Great on 2010-02-19
Open a terminal, type "top" (without the quotes) and post the output.

---

### Post by tom.swartz07 on 2010-02-19
> **ThePinkWitch said:**
> I tried to install a program with sudo aptitude install and it worked but it got stuck for 15 mins trying to download a file so I just closed the terminal. I have had problems all afternoon with downloads to update my software packages. They have been getting stuck on downloading even tho my internet is working fine to use the browser. Anyway I need to shut down the apt process in the terminal. Can someone tell me how to do that pls :)

just run ```
killall aptitude
```

That will stop the process, then you could run the other commands to refresh it. 


Alternatively, you could just log out or restart to kill the process.

---

### Post by audiomick on 2010-02-19
> **tom.swartz07 said:**
> just run ```
killall aptitude
```That will stop the process, then you could run the other commands to refresh it. 


Alternatively, you could just log out or restart to kill the process.
This should work.
If you want to see what is running, open
system> administration> system monitor
and look for it there under "processes". You should be able to select it and kill it from there too, I think.

---

### Post by tom.swartz07 on 2010-02-19
> **audiomick said:**
> This should work.
If you want to see what is running, open
system> administration> system monitor
and look for it there under "processes". You should be able to select it and kill it from there too, I think.

if youre running in a command line environment, you could achieve the same effect by running 
```
ps xf
```

Itll print a tree of all of your processes, allowing you to see what program has what processes running- you could then see what the process is called to kill it

---

### Post by ThePinkWitch on 2010-02-19
> **audiomick said:**
> This should work.
If you want to see what is running, open
system> administration> system monitor
and look for it there under "processes". You should be able to select it and kill it from there too, I think.

HI :) I turned the computer off because I had to go out and you were right it was sorted when I got back and turned it on. THANKYOU EVERYONE :)

---

### Post by ThePinkWitch on 2010-02-19
> **tom.swartz07 said:**
> just run ```
killall aptitude
```

That will stop the process, then you could run the other commands to refresh it. 


Alternatively, you could just log out or restart to kill the process.

Thanks you were right. Turning it on then off fixed it ;)

---

