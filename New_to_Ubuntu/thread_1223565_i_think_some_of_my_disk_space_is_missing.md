---
title: "i think some of my disk space is missing"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-26
i recently did a fresh-alternative-encrypted install but i think some of my disk space is missing
opening the "Disk usage Analyzer" it shows me that my "total filesystem capacity" is 107.2 gb.
but  my hard drive is a 120 gb one
where is the rest of my disk space?

---

### Post by Liolikas on 2009-07-26
120Gb hdd is advertising really it is less. 120 really is only ~111Gb.

---

### Post by heyyy on 2009-07-26
> **Liolikas said:**
> 120Gb hdd is advertising really it is less. 120 really is only ~111Gb.

nope i dont think so because on my previous installs the amount was 119.8 gbs

---

### Post by Liolikas on 2009-07-26
I do not like tat analyzer df -h and calculate sum of everything.
Also open gparted and look for unformatted space.

---

### Post by heyyy on 2009-07-26
is there a command to type ,so i can post the output here?

---

### Post by Liolikas on 2009-07-26
df -h
and
scrot
makes images but you have to install scrot first.

---

### Post by philinux on 2009-07-26
Post #4

```
df -h
```

---

### Post by heyyy on 2009-07-26
df -h:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/user-root
                      107G  4.4G   98G   5% /
tmpfs                 502M     0  502M   0% /lib/init/rw
varrun                502M  116K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  152K  502M   1% /dev
tmpfs                 502M   88K  502M   1% /dev/shm
lrm                   502M  2.2M  500M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda5             228M   27M  189M  13% /boot
/home/user/.Private
                      107G  4.4G   98G   5% /home/user

```

---

### Post by heyyy on 2009-07-26
i dont know how scrot works

---

### Post by Liolikas on 2009-07-26
> **heyyy said:**
> i dont know how scrot works
You type it in you get screen-shot in *.png: simple.

df -h really shows 107Gb nothing new.
Look in gparted maybe you left some as unformatted?

---

### Post by hrod beraht on 2009-07-26
In general, an ext formatted drive won't show the full capacity even when empty because, by default, ext reserves 5% disk space for root.
From *man tune2fs*:
> **-m reserved-blocks-percentage**
              Set the percentage of the filesystem which may only be allocated by privileged processes.   [color=#800000]Reserving some number of filesystem blocks  for  use  by  privileged
              processes  is  done  to  avoid filesystem fragmentation, and to allow system daemons, such as syslogd(8), to continue to function correctly after non-privileged
              processes are prevented from writing to the filesystem.  Normally, the default percentage of reserved blocks is 5%.
[/color]
**-r reserved-blocks-count**
              Set the number of reserved filesystem blocks.

You can disable it after-the-fact by using the command:
```
tune2fs -r 0 /dev/sdx (or hdx or whatever is appropriate on your system)
```
or by just using *-m 0* when first formatting it.

But, **I don't recommend disabling it**. It's sometimes appropriate on, say, an external usb drive, but for your primary boot drive, it's there for a reason (see above) and is actually a good thing :)

Although in your case, I'd bet that the encryption is using some of it as well.

Bob

---

