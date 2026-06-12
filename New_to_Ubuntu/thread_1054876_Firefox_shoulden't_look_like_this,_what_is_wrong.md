---
title: "Firefox shoulden't look like this, what is wrong"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-01-30
It's something that is very weird with firefox, from time to time do something happen that it turn out as can been seen in the attachment.

---

### Post by pluckypigeon on 2009-01-30
> **SpinningAround said:**
> It's something that is very weird with firefox, from time to time do something happen that it turn out as can been seen in the attachment.

You aren't by any chance using an Intel Chip for your graphics?

---

### Post by Lunx on 2009-01-30
Havn't got much of an explanation why FF looks like that, but one suggestion would be to try another browser and see how that goes, then you'll at least have some idea whether it's your FF installation itself that's not playing nicely. I use Opera as my browser and it runs well in Ubuntu.

---

### Post by ellalan on 2009-01-30
No, please whatever you do, do not touch Opera. It is the worst browser one could have in their PC.
They expect the customer to know their browser better than themselves, the forums are very rude and they do not provide any help.

---

### Post by timcredible on 2009-01-30
you could try removing and then re-adding firefox.  if that doesn't work, you could use epiphany (gnome-ized version of firefox, in the repos).

---

### Post by mrbiggbrain on 2009-01-30
> **ellalan said:**
> No, please whatever you do, do not touch Opera. It is the worst browser one could have in their PC.
They expect the customer to know their browser better than themselves, the forums are very rude and they do not provide any help.

so its like Vi?

---

### Post by donkyhotay on 2009-01-30
Strange, maybe a graphics card issue. Do you have any problems with any other programs (even if you don't think it's related)? If you have no other problems then with firefox I would try reinstalling it as mentioned above.

---

### Post by doktorrr on 2009-01-30
> **ellalan said:**
> No, please whatever you do, do not touch Opera. It is the worst browser one could have in their PC.

Internet explorer is worst browser ever made.

---

### Post by LowSky on 2009-01-30
Stop arguing about who makes the worse browser
First back up your bookmarks, then Go to /home/.mozilla folder, delete the contents of the firefox folder, and that should correct the issue.

---

### Post by tahitiwibble on 2009-01-30
> **LowSky said:**
> Stop arguing about who makes the worse browser
First back up your bookmarks, then Go to /home/.mozilla folder, delete the contents of the firefox folder, and that should correct the issue.

The Foxmarks add on is **really** great for backing up bookmarks and passwords. :)

---

### Post by LowSky on 2009-01-30
You can back up bookmark from firefox easily, why do you need an addon for that?

go to bookmarks>organize bookmarks and then choose backup or export, simple as that

---

### Post by Gulyan on 2009-01-30
> **ellalan said:**
> No, please whatever you do, do not touch Opera. It is the worst browser one could have in their PC.

Opera is one of the best (if not _the_ best) browsers ever made.
The worst is by far internet explorer :popcorn:

---

### Post by tahitiwibble on 2009-01-30
> **LowSky said:**
> You can back up bookmark from firefox easily, why do you need an addon for that?

go to bookmarks>organize bookmarks and then choose backup or export, simple as that

I think it's fantastic that Foxmarks backs up both bookmarks and passwords **automatically** to a remote server ........ and the fact of being able to access your bookmarks and passwords from any computer you happen to come across running FF is priceless.

---

### Post by pluckypigeon on 2009-01-30
> **donkyhotay said:**
> Strange, maybe a graphics card issue

I don't think he cares anymore. Either that or his computer broke.

I had a similar problem with my card but it wasn't just Firefox. Bits of windows would disappear. 

I use the, well known for problems with Linux, Intel 82845G/GL [Brookdale-G] Chipset. 

I had to disable acceleration.

---

### Post by walkerk on 2009-01-30
You can try removing your user preferences and starting it fresh...

```
rm -rf ~/.mozilla/firefox
```

---

### Post by SpinningAround on 2009-01-31
> **LowSky said:**
> Stop arguing about who makes the worse browser
First back up your bookmarks, then Go to /home/.mozilla folder, delete the contents of the firefox folder, and that should correct the issue.

Have done that will see how it turns out :)

---

### Post by Revenged on 2009-01-31
> **ellalan said:**
> No, please whatever you do, do not touch Opera. It is the worst browser one could have in their PC.
They expect the customer to know their browser better than themselves, the forums are very rude and they do not provide any help.

I don't know what you're talking about. I've never had any issues at all with opera. Used it for years on Windows. Firefox was a bit confusing when I switched over.

Opera has a lot of little features and such that you do need to know the browser quite well to use, but you don't have to use these.

---

### Post by smashblock on 2009-01-31
> **LowSky said:**
> Stop arguing about who makes the worse browser

I agree.
Its obviously internet explorer.

---

### Post by IEKnight on 2009-02-21
Just had the same problem - Here's how I fixed it:

1. Open Firefox.
2. Press F11 to switch to full-screen, and again to bring it back.
3. Minimise and restore the window.

Now it will look normal, but if you close firefox and start it again, the problem is back. To get rid of it for good:

4. Once you're at step 3, un-maximise the window.
5. If you can't see the titlebar, repeat step 2.
6. You should see a part, if not all of the titlebar. Drag it so you can see the whole thing.
7. Resize so the whole window fits on your screen.
8. Close Firefox, and re-open it.

The window should now look normal. To tidy up:

9. Maximise the window.
10. Close Firefox, and re-open it.

Problem should be fixed ;) .

Hope that helped.

---

### Post by frank002 on 2009-02-21
Go to  System>Preferences>CompizConfigSettingsMgr.. Once there go to Utility>Workarounds and uncheck the box that says Legacy Fullscreen Support. That should fix the problem.

---

