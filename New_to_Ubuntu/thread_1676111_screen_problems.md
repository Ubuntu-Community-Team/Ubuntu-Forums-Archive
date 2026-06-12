---
title: "screen problems"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by sa-mejia on 2011-01-26
Today, I made a fresh install of Ubuntu Lynx 10.4, and it turns out that my screen, which had worked perfectly for years with the last LTS version, is now somewhat hazy, everything looks a bit blurred.

When I go to the monitor preferences I find that the resulution is all right (1280x800).  This is the resolution that my device has in windows, in which everything looks sharp and clear.

Under my lspci this seems to be the entry for my video card:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)


How shall I begin addressing and solving the problem... I really need to fix it: I am getting a headache after 30 minutes in front of my screen.

S.

---

### Post by Bölvaður on 2011-01-26
can you provide us with a screenshot?

---

### Post by sa-mejia on 2011-01-26
Sure.

[ATTACH]182032[/ATTACH]

Let me know if the image displays correctly.

---

### Post by Bölvaður on 2011-01-27
> **sa-mejia said:**
> Let me know if the image displays correctly.
It does not, the image is too heavily compressed and shrunk down. Please just use the png file that comes out from taking the screenshot and if it is too big you can upload it to dropbox and have it there for 1-2 days.

But if I had to guess, it looks ok.
Have you tried other monitors? This seems kind of silly to me right now, but I guess at the end of this we'll have figured it out.

---

### Post by sa-mejia on 2011-01-29
Thanks for your help.  My wife also believes that I am making a fuss out of nothing.  But I am still inclined to think that the quality of the screen is worse than my windows appearance and my prior ubuntu appearance. 

I have attached the screenshot again, through a Dropbox link. 

[http://dl.dropbox.com/u/1143164/Screenshot.png](http://dl.dropbox.com/u/1143164/Screenshot.png)

I will keep using it as for the time being (instead of switching to windows) and perhaps will get used to it.

---

### Post by Bölvaður on 2011-02-05
Your screenshot does not show anything blurred, so we have narrowed down the problem.
You can confirm that by checking that screenshot on another machine.

The only graphical anomaly I saw was because you zoomed in firefox, but it did not blur the image at all, it just make it even more obvious the pixels if anything.

Not sure where to begin. The driver might be the first thing to check.
Also turn off all desktop effects and see if it changes anything.
When you boot your computer up in "rescue mode" (you can find it in grub). Fill the screen with text and then check if it is blurred. This might be the easiest and most useful way to find out where the problem lies.

---

### Post by sa-mejia on 2011-02-09
Bolvadur, thanks a lot for your responses... I have turned off the Desktop effects, and it seems to have improven a bit...  Anyhow, I have gotten used to my new screen and seem to be OK working with it now.  

I am beginning to believe that my wife is right, that everything displays nicely.  That I just found the graphic environment of 10.4 odd, and I have wrongly identified such oddness as the screen being blurred.

Do you have any idea of how can I increase the brightness of the screen (The brightness status bar is already at its maximum, but I seem to find it still quite opaque).

---

### Post by Bölvaður on 2011-02-11
after quick googling I found this
```

$ xgamma -gamma 1.0
```


this command changes the xserver but only for this one session, I dont think it's stored in any config file like most commands like this. The value 1.0 is of course the default one and to increase brightness you should do something liket his:
```

$ xgamma -gamma 1.5
```

---

### Post by sa-mejia on 2011-02-23
Great... thanks

---

