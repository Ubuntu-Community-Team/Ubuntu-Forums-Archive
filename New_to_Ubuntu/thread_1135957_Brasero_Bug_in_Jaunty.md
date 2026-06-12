---
title: "Brasero Bug in Jaunty"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-04-24
So, basically I want to burn a number of avi files onto a dvd. I am burning this as a data dvd using the default brasero application that ships with jaunty.

The first time I tried it the burning dvd (small) window opened and immediately closed.

The second time I disabled "burnproof" and the window was there and it started, but going at about 0.3 KiB/s when my DVDs are 8x and I'm sure my DVD burner is faster (in fact in intrepid it was much faster)

The third time I have disabled "burnproof" and "compatibility with windows", speed is still 0.3.

Any ideas?

---

### Post by abhiroopb on 2009-04-24
Update: Brasero just restarted... :S

---

### Post by ubuntu27 on 2009-04-25
I have not tried burning a DVD using Brasero.

if you want to create a DVD movie, you will have to convert your avi to an **mpeg** file first.
I don't know what other formats supports. But Avi is definitely NOT one of them.

After converting you can burn it with any burning software.



This has always been true. I do not know if the new application in Jaunty supports avi now.

---

### Post by bennachie on 2009-04-25
Burning a data DVD, when the project comprises a large number of relatively small files, is, in my limited experience, a tedious process in Brasero, being MUCH slower than any of the normal Windows burning packages.

Fairly obviously, you are most unlikely to achieve the nominal burn speed of the drive in such circumstances, but I would like to hope that somebody is working on improving the situation.

---

### Post by Didius Falco on 2009-04-25
For a two-step workaround, you could make the data files into an .iso first, then burn that to the cd/dvd:

```
mkisofs -r -o file.iso /location_of_folder/
```

---

### Post by abhiroopb on 2009-04-25
> **ubuntu27 said:**
> I have not tried burning a DVD using Brasero.

if you want to create a DVD movie, you will have to convert your avi to an **mpeg** file first.
I don't know what other formats supports. But Avi is definitely NOT one of them.

After converting you can burn it with any burning software.



This has always been true. I do not know if the new application in Jaunty supports avi now.

If you notice I said I'm burning it as a **DATA DVD**. So the file format is irrelevant.

---

### Post by abhiroopb on 2009-04-25
> **bennachie said:**
> Burning a data DVD, when the project comprises a large number of relatively small files, is, in my limited experience, a tedious process in Brasero, being MUCH slower than any of the normal Windows burning packages.

Fairly obviously, you are most unlikely to achieve the nominal burn speed of the drive in such circumstances, but I would like to hope that somebody is working on improving the situation.

In this case I had about 20 200mb files...so this should be the case at all.. and like I said it was fine before.

---

### Post by abhiroopb on 2009-04-25
> **Didius Falco said:**
> For a two-step workaround, you could make the data files into an .iso first, then burn that to the cd/dvd:

```
mkisofs -r -o file.iso /location_of_folder/
```

Thanks for that but its not really feasible. Actually I downloaded gnomebaker and used it, and everything worked without a problem.

I'm quite shocked that considering brasero was one of the heavily touted features, it seems to have a major bug!

---

### Post by NightwishFan on 2009-04-25
It works fine on my drive. Try another burning application such as k3b or gnomebaker, and see if your problem still exists.

As for burn-proof, that ensures that you do not have any buffer underruns, and if your drive does not support it, it should not work in any case, I do not think it would be able to be enabled.

If you are burning some DVDs, there is a final step called finalizing which seems to take long with no progress bar, that is normal.

---

### Post by abhiroopb on 2009-04-25
Yea I tried gnomebaker and burnt about 5 DATA DVDs with videos on them, all worked without a problem.

---

### Post by NightwishFan on 2009-04-25
That is disappointing.. I thought this release was more stable than before. One thing that irks me is I believe Brasero uses a "backend" command line program, such as genisoimage. I would think Gnomebaker and K3b would do the same, which means the problem lies with the interface of brasero.

---

### Post by ubuntu27 on 2009-04-25
You should fill a bug report"

[https://bugs.launchpad.net/brasero](https://bugs.launchpad.net/brasero)

---

