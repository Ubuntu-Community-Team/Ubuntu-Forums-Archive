---
title: "google earth"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by baldydash on 2009-02-25
i've downloaded and managed to install google earth 5.0 for linux when i open it a box comes up saying could not create folder the another Notice box that google earth could not write to current cache or myplaces file any way round this?

---

### Post by taurus on 2009-02-25
Did you install it as root, sudo?  Try to install it as a regular user in your $HOME directory.

---

### Post by jtmedin on 2009-02-25
I seem to be in the same fix as the original poster. I downloaded 5. & got G*.bin on the desktop. I installed using the terminal with:
chmod +x G*.bin
./G*bin

when it started

got the message about unable /root/.googleearth/Cache
after ok got the message about using Cache ... in my home ...

When i start googleearth it starts up with a nice picture of earth then a couple of quick windows about tips ... then disappears HELP!

---

### Post by binbash on 2009-02-25
you need to rename libcrypto.so.0.9.8 : 

[http://ubuntushell.blogspot.com/2009/02/howto-install-google-earth-50-beta-on.html](http://ubuntushell.blogspot.com/2009/02/howto-install-google-earth-50-beta-on.html)

---

### Post by baldydash on 2009-02-25
tried to run and install with $.GoogleEarthLinux.bin but comes back with command not found

---

### Post by Therion on 2009-02-25
I just installed it (Google Earth) from the Google repo and it works fine...  

Is the repo-version totally outdated or something that you guys are installing from source?

---

### Post by taurus on 2009-02-25
> **baldydash said:**
> tried to run and install with $.GoogleEarthLinux.bin but comes back with command not found

Make sure you are in the right directory or you have to include the whole path.  If you saved it to your desktop, then you need to change to that first.

```
cd ~/Desktop
```

> **Therion said:**
> I just installed it (Google Earth) from the Google repo and it works fine...  

Is the repo-version totally outdated or something that you guys are installing from source?

I think some people just want the newest or the latest and they can't wait for it to hit the repos (Medibuntu).

---

### Post by Therion on 2009-02-25
> **taurus said:**
> I think some people just want the newest or the latest and they can't wait for it to hit the repos (Medibuntu).
No, I meant the Google-repo:

[http://www.google.com/linuxrepositories/scripted.html](http://www.google.com/linuxrepositories/scripted.html)

I thought that was the latest & greatest (for Google Earth (the only thing I want from that repo))...  No??

---

### Post by jtmedin on 2009-02-25
ok thanks but cp would not do the rename so i had to use mv then it works thanks again

---

### Post by clemm on 2009-02-25
I am not sure if this is your problem, but I have had problems with downloads as well.
I found before I could do anything I had to click on the file properties,
select permissions, and change the default from read only to read and write. You have to have the root password to change that. 
My problem with Google earth is it starts up, goes the tips window and Google earth as normal. Then it goes full screen, then it immediately closes,? This is on both the 4.x and the newest 5.X version.
If anyone knows how to fix that please post or email [email]clemm17@hotmail.com[/email]
Thanks

---

