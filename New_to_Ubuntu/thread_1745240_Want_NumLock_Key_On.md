---
title: "Want NumLock Key On"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by tb75252 on 2011-04-30
I am using Ubuntu 10.10 (32-bit).

Is there a way to turn the NumLock key on _before_ the login screen?  Right now, it only turns automatically on after the login screen...

I have NumLock enabled in my BIOS and I even have installed "numlockx".  Bat that does not help.

---

### Post by wojox on 2011-04-30
```
sudo cp /etc/gdm/Init/Default /etc/gdm/init/Default_backup
```
```
gksudo gedit /etc/gdm/Init/Default
```

* Find this line

```
exit 0
```

*Add the following line above it

```
/usr/bin/numlockx on
```

---

### Post by bug67 on 2011-04-30
This is what worked for me:

[http://ubuntuforums.org/showpost.php?p=10495922&postcount=4](http://ubuntuforums.org/showpost.php?p=10495922&postcount=4)

---

### Post by oklokl on 2011-05-01
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

sudo gedit /etc/gdm/Init/Default

```
[COLOR=#0900FF]# Set numlock on in GDM[/COLOR][COLOR=#0900FF]echo "Setting numlock on in GDM"[/COLOR]
[COLOR=#0900FF]GDM_INIT=/etc/gdm/Init/Default[/COLOR]
[COLOR=#0900FF]if [ -f $GDM_INIT ]; then[/COLOR]
[COLOR=#0900FF]  if ! grep -q numlockx $GDM_INIT ; then[/COLOR]
[COLOR=#0900FF]    sed -i 's/^exit 0/test -x \/usr\/bin\/numlockx \&\& \/usr\/bin\/numlockx on\nexit 0/g' $GDM_INIT[/COLOR]
[COLOR=#0900FF]  fi[/COLOR]
[COLOR=#0900FF]fi[/COLOR]
[COLOR=#0900FF]if [ -x /usr/bin/numlockx ]; then[/COLOR]
[COLOR=#0900FF]  /usr/bin/numlockx on[/COLOR]
[COLOR=#0900FF]fi[/COLOR]

```
Does not turn on [COLOR=#0900FF]numlock
[/COLOR]Enabled

---

### Post by wolfen69 on 2011-05-01
You can go into most BIOS's and choose to have Numlock enabled.

---

### Post by tb75252 on 2011-05-02
> **wojox said:**
> ```
sudo cp /etc/gdm/Init/Default /etc/gdm/init/Default_backup
``````
gksudo gedit /etc/gdm/Init/Default
```* Find this line

```
exit 0
```*Add the following line above it

```
/usr/bin/numlockx on
```


Unfortunately it does not work for me.  I have numlockx installed and I copy/pasted the code as you gave it to me but NumLock still stays off before the login screen.  After I am past the login screen, NumLock turns on.

Maybe it is because I have old hardware.  (11-year old desktop...)

---

### Post by tb75252 on 2011-05-02
> **bug67 said:**
> This is what worked for me:

[http://ubuntuforums.org/showpost.php?p=10495922&postcount=4](http://ubuntuforums.org/showpost.php?p=10495922&postcount=4)


As I was just telling wojox, this method unfortunately does not work for me...

---

### Post by tb75252 on 2011-05-02
> **oklokl said:**
> [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

sudo gedit /etc/gdm/Init/Default

```
[COLOR=#0900ff]# Set numlock on in GDM[/COLOR][COLOR=#0900ff]echo "Setting numlock on in GDM"[/COLOR]
[COLOR=#0900ff]GDM_INIT=/etc/gdm/Init/Default[/COLOR]
[COLOR=#0900ff]if [ -f $GDM_INIT ]; then[/COLOR]
[COLOR=#0900ff]  if ! grep -q numlockx $GDM_INIT ; then[/COLOR]
[COLOR=#0900ff]    sed -i 's/^exit 0/test -x \/usr\/bin\/numlockx \&\& \/usr\/bin\/numlockx on\nexit 0/g' $GDM_INIT[/COLOR]
[COLOR=#0900ff]  fi[/COLOR]
[COLOR=#0900ff]fi[/COLOR]
[COLOR=#0900ff]if [ -x /usr/bin/numlockx ]; then[/COLOR]
[COLOR=#0900ff]  /usr/bin/numlockx on[/COLOR]
[COLOR=#0900ff]fi[/COLOR]

```Does not turn on [COLOR=#0900ff]numlock
[/COLOR]Enabled


Unfortunately your solution does not seem to work for me...  NumLock stays off before the login screen and turns on only after I am logged in.

---

