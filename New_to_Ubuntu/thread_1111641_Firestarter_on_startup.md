---
title: "Firestarter on startup"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-03-30
hey, i want to have Firestarter start up when i turn on my computer. now to this, what code would i need to start it.

i was thinking  *sudo Firestarter* but im not to sure can any one help me with this please
TYVM!!!!

     Ravernomina

---

### Post by abn91c on 2009-03-30
go to the session manager>add program then type **gksu /usr/sbin/firestarter** where it ask for to enter command to start program

---

### Post by Ravernomina on 2009-03-30
ay thank you :) btw what does *gsku* mean?

---

### Post by abn91c on 2009-03-30
> **Ravernomina said:**
> ay thank you :) btw what does *gsku* mean?
not sure but it launches my firerwall GUI here is a Pic

---

### Post by Ravernomina on 2009-03-30
hmm shot in the dark here maybe something with the Deamond for firestarter :o

---

### Post by jakupl on 2009-03-30
You do not need to start firestarter on boot. Firestarter is not an actual firewall, only a configuration tool. And gksu is like sudo, but it works better on graphical programs.

---

### Post by kansasnoob on 2009-03-30
You would also have to edit sudoers:

[https://help.ubuntu.com/community/Sudoers#The%20Default%20Ubuntu%20Sudoers%20File](https://help.ubuntu.com/community/Sudoers#The%20Default%20Ubuntu%20Sudoers%20File)

More here:

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

IMHO I'd remove Firestarter altogether and install GUFW which is available in Synaptic from Intrepid forward. If you're using Hardy you can get it here:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Then go to System > Administration > Firewall Configuration and you'll see this:

[ATTACH]108122[/ATTACH]

Just tick "Firewall Enabled" and don't worry! Don't change anything else!

---

### Post by Ravernomina on 2009-03-31
you sure cuz firestarter does block  Bad Ips :)

---

### Post by philinux on 2009-03-31
Yes but once you've used it to set up what you want there's no need to run it at startup. It's done it's job which is to modify THE firewall which is iptables which runs in the background all the time.

---

### Post by hyper_ch on 2009-03-31
I doubt you need firestarter at all...

---

### Post by ivanvajar on 2009-03-31
Yeah! Who needs Firestarter! Linux doesn't have ANY faced-out processes.

---

### Post by Ravernomina on 2009-04-02
still it makes life easy to see what all your bandwith is going to :)

---

### Post by xpod on 2009-04-02
> still it makes life easy to see what all your bandwith is going to 

You may find some of the tools here useful for that.
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)


Or you could install conky and have it do a similar job.
[ATTACH]108424[/ATTACH]

---

