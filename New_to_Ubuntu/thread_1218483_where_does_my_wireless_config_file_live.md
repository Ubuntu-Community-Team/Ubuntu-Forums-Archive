---
title: "where does my wireless config file live?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by muteXe on 2009-07-20
Morning,
When i type wireless related stuff into the gui dialog (such as my wpa key and essid name for example), where is this information actually stored?  Somewhere in /etc perhaps?

Many thanks,

mute

---

### Post by muteXe on 2009-07-21
Someone out there must know this :o

---

### Post by ddrichardson on 2009-07-21
~/.gconf/system/networking/connections/

---

### Post by muteXe on 2009-07-21
AH nice one, I shall check when i get home.

Cheers mate.

---

### Post by ayenack on 2009-07-21
In Terminal.

**sudo nano /etc/network/interfaces**

This will show your network interfaces config file.

---

### Post by ddrichardson on 2009-07-21
> **ayenack said:**
> In Terminal.

**sudo nano /etc/network/interfaces**

This will show your network interfaces config file.
Yes but don't bother editing it because it's managed (indeed overwritten) bu NetworkManager and has been (unless you make it immutable) for quite some time.

---

### Post by ayenack on 2009-07-21
> **ddrichardson said:**
> Yes but don't bother editing it because it's managed (indeed overwritten) bu NetworkManager and has been (unless you make it immutable) for quite some time.

Edit:- My mistake misread your post.

He's running 8.04 don't think this applies. Not sure though.

What I should have said is that ~/.gconf/system/networking/connections/ isn't present on 8.04 I don't think. Or if it is its certainly not present on my setup with wireless.

---

### Post by muteXe on 2009-07-21
Thx for the replies all.
Found some info in
```

~/.gconf/system/networking/wireless/networks

```
and not very much in 
```

/etc/network/interfaces

```

Cheers :)

---

