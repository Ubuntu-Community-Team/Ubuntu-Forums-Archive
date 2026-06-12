---
title: "crontab-don't work,reboot command"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by joker@ on 2010-11-06
I have small problem with crontab,i want to reboot my system every 3:00,So i add "reboot" command to cron

```
  crontab -e                     

# m h  dom mon dow   command
  * 3  *   *   *     reboot


```

File is in there 

```
File: /tmp/crontab.OgX3KE/crontab
```

But is not rebooting at all,why?Anyone can help me?

---

### Post by Hippytaff on 2010-11-06
did you update cron as root?

---

### Post by Barriehie on 2010-11-06
How about:
```

* 3  *   *   *     root shutdown -r now
```

---

### Post by Hippytaff on 2010-11-06
> **Barriehie said:**
> How about:
```

* 3  *   *   *     root shutdown -r now
```

That should do it :-)

forgot I had reboot as an alias in .bashrc

---

### Post by Barriehie on 2010-11-06
> **Hippytaff said:**
> That should do it :-)

forgot I had reboot as an alias in .bashrc

I hate when that happens; been there done that, rebooted twice... ;)

---

### Post by joker@ on 2010-11-06
> **Hippytaff said:**
> did you update cron as root?

Mean..
```
crontab -u root -e
```
?
Yes i done like this,maybe wrong

@Barriehie

I want just reboot,shutdown command will switch off computer without wakeup.

---

### Post by Barriehie on 2010-11-06
> **joker@ said:**
> Mean..
```
crontab -u root -e
```
?
Yes i done like this,maybe wrong

@Barriehie

I want just reboot,shutdown command will switch off computer without wakeup.

shutdown -h will halt and shutdown -r will reboot. ;)

---

### Post by joker@ on 2010-11-08
Still dont want reboot,cron changed to vaule as above and nothing

---

### Post by Hippytaff on 2010-11-08
If you want crontab to run the command then it should work by just adding
```

* 3  *   *   *     root shutdown -r now 
```
to the cron file. if you want cron to run a script, you need to point cron at the script
```

* 3 * * * /path/to/relevant/script.sh

```

---

### Post by toekneewood on 2010-11-08
For the reboot command to work on crontab you have to put the path to the binary that lives in /sbin/shutdown like so:
```

15 23 * * *  /sbin/shutdown -h now

```

---

### Post by Hippytaff on 2010-11-08
> **toekneewood said:**
> For the reboot command to work on crontab you have to put the path to the binary that lives in /sbin/shutdown like so:
```

15 23 * * *  /sbin/shutdown -h now

```
 
Really? I thought you could just run the command :-s
 
Learned something new here too...cheers :-)

---

### Post by CharlesA on 2010-11-08
> **Hippytaff said:**
> Really? I thought you could just run the command :-s
 
Learned something new here too...cheers :-)

Crontab doesn't normally share yer envirnomental variables, so it's best to use the full path (or test and see what you can and can't do without the full path)

---

### Post by Hippytaff on 2010-11-08
> **CharlesA said:**
> Crontab doesn't normally share yer envirnomental variables, so it's best to use the full path (or test and see what you can and can't do without the full path)
 
I'll have a play with that after work :-)

---

