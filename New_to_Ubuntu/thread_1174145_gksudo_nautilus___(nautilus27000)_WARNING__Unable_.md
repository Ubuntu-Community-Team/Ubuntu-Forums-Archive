---
title: "gksudo nautilus  ** (nautilus:27000): WARNING **: Unable to add monitor: Operation no"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by YQ002lc2 on 2009-05-30
Dear Friends, 

I'll just keep it short and sweet and post what was in the terminal. I originally found out to try installing samba from [http://ubuntuforums.org/archive/index.php/t-908279.html](http://ubuntuforums.org/archive/index.php/t-908279.html)

               So here goes:
ran: 
gksudo nautilus

Got:
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

ran:
sudo apt-get install samba
// Suffice it to say it installed properly and fixed the first problem

then ran:
gksudo nautilus

Got:
** (nautilus:27000): WARNING **: Unable to add monitor: Operation not supported

Does anyone know how to fix this?
Thanks,

jpinson

---

### Post by YQ002lc2 on 2009-05-30
Update, 

Whenever I do sudo nautilus, gksudo nautilus, gksu nautilus, I get similar messages.

They all look something like this: 

** (nautilus:30563): WARNING **: Unable to add monitor: Operation not supported

The number changes everytime, but it's always the same message.

Then there's usually something like this when I close nautilus:

--- Hash table keys for warning below:
--> file:///root

(nautilus:31018): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:31018): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

The list of hash table keys changes depending on what browse while it's open.

Thanks,

jpinson

---

### Post by YQ002lc2 on 2009-05-31
I found this link:
[http://ubuntuforums.org/showthread.php?t=849147&highlight=unable+add+monitor](http://ubuntuforums.org/showthread.php?t=849147&highlight=unable+add+monitor)

I tried what ronacc suggested and it temporarily worked to remove the monitor message problem. At least, it worked the first time I ran gksudo nautilus in my session.
The second time I ran gksudo nautilus, it was back to the same problems as above. 

I seem to be able to do everything without a problem when using any of the gksudo, sudo, or gksu commands, and there is no error displayed except when I run nautilus with them. 

So, all in all, it seems this is a benign problem, but it's annoying none the less. 

Also, I ran the gksudo nautilus command on my Lenovo T60p and did not get any error message except for the hash table keys when I closed. The unable to add monitor message was not there. 

The Unable to add monitor error seems to only occur on my Dell Latitude D600 computer. I upgraded from Ubuntu 8.10 to 9.04 on the Lenovo. I reimaged totally on the Dell. The lenovo uses ext3 while the Dell uses ext4.

I don't know if any of this information will help. I hope this problem will be fixed one day. If someone finds a solution, please post it here. 

Thanks,

jpinson

---

### Post by Bearly Able on 2009-05-31
I get the same messages, and I'm not using a Dell.  I upgraded from 8.04 to 9.04 (via 8.10), but as far as I can recall, the error messages precede the update.  As you say, they don't seem to prevent me doing anything.

---

### Post by coldmack on 2009-06-01
I guess I am having a similar problem except when I type in sudo nautilus I get no message and nothing even opens up.

---

### Post by Bearly Able on 2009-06-01
coldmack: you need to use gksudo with nautilus.  As i understand it, you use sudo when working in the terminal, but gksudo for GUI applications.

---

### Post by braete on 2009-06-01
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by Bender2k14 on 2009-06-01
> **jpinson said:**
> The number changes everytime, but it's always the same message.

The number is the Process ID (PID), which is a unique number given to each process.

---

### Post by dBuster on 2009-06-01
Have you tried to [alt][F2] and then enter "gksu nautilus"  Do you get any errors or does it open properly for you?  

If I open from a terminal window I get an error but when I alt+F2 it works without throwing me an error anywhere.

---

### Post by YQ002lc2 on 2009-06-01
Thank you all for your posts.

To Bender2k14:
Thanks for the information about that number being the process ID. 

To dBuster:
Hitting Alt+F2 and running gnome-terminal I get the same behavior.

To All (an update):
It seems that on my Lenovo, I don't get the monitor message the first time I run gksudo nautilus, but after I close and run it a second time, I get the monitor message. Each time I restart the terminal, the monitor message does not appear the first time, but appears subsequent times. Also, the hash table keys are still there regardless of how I start the terminal.
For some reason, though, the monitor message always appears on my Dell laptop. 


Thanks,

jpinson

---

### Post by Bender2k14 on 2009-06-01
> **jpinson said:**
> Update, 

Whenever I do ... gksudo nautilus, ...

** (nautilus:30563): WARNING **: Unable to add monitor: Operation not supported

...

Then there's usually something like this when I close nautilus:

--- Hash table keys for warning below:
--> file:///root

(nautilus:31018): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:31018): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

I have the same error messages, but I think nautilus is working fine.  I am not trying to do anything with Samba though.  Is this the only thing that is "not working as expected" right now?...because I am guessing that you can ignore this without any problems.

---

### Post by coldmack on 2009-06-01
> **Lesley Lutomski said:**
> coldmack: you need to use gksudo with nautilus.  As i understand it, you use sudo when working in the terminal, but gksudo for GUI applications.
I have tired it all the ways suggested and still nothing. Thanks though.

---

### Post by Bender2k14 on 2009-06-01
> **coldmack said:**
> I guess I am having a similar problem except when I type in sudo nautilus I get no message and nothing even opens up.

Do you get a new prompt or do you have to do a ctrl-c?

---

### Post by rbueno on 2009-06-04
> **Lesley Lutomski said:**
> coldmack: you need to use gksudo with nautilus.  As i understand it, you use sudo when working in the terminal, but gksudo for GUI applications.
i used gksudo when editing files in root document. ex. /var/www/mydirectory. it gives permission to me to edit, ad and paste files.(mine php).. i guess the error is not by the brand of computers but maybe the installation process.

Try this:
1. uninstall nautilus
2. restart pc.(some application need pc restarting to complete)
3. reinstall nautilus. Avoid install another application.
4. restart pc.

Tips:
if still not working, try ***gksudo gedit nautilus***.

hope this can help :D
Best regards,

---

