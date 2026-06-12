---
title: "restore home directory upon login"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by alphaakenny1 on 2009-01-06
I have a guest account on my computer and have it perfectly set for "guests".  Unfortunately, sometimes the guests do stuff to it that mess it up.  So I was wondering if there is a way to make sure this is how that account remains.  I was thinking something like everytime somebody logs into that account the computer extracts a file and restores the home directory to a previous time (or maybe upon logging out).  Something like they do at universities and schools and how all the settings are restored at each login.

---

### Post by jken146 on 2009-01-06
The guest account in intrepid does this.

---

### Post by albinootje on 2009-01-06
> **alphaakenny1 said:**
> I have a guest account on my computer and have it perfectly set for "guests".  Unfortunately, sometimes the guests do stuff to it that mess it up.

If you don't use Ubuntu Intrepid, you can use the following construction to restore the guest home directory after a reboot.

1) Make sure you have everything configured, and the guest user is not logged in.
2) Make an archive of /home/guest :
```

cd /etc/
sudo tar czvf /home/guest guest.tgz
sudo chmod 600 guest.tgz

```

3) Add the following to /etc/rc.local (Read first the content of /etc/rc.local !)

```

rm -rf /home/guest
cd /home
tar xzvf /etc/guest.tgz
cd

```

Of course you can also run /etc/rc.local (sudo /etc/rc.local) yourself after your guests are gone ;-)

---

### Post by alphaakenny1 on 2009-01-06
Thank you, I use hardy so this works perfectly

---

