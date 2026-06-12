---
title: "Really Wanted to Give Unbuntu a try"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by nortongene on 2011-08-03
I just installed Unbuntu and am really happy with it minus I can not load programs I use like Reason, CyberLink Power Director, and other things like that.  I have most of the ISO or exe files and read about using wine.  However I get an error message everytime I try to load them.  I really don't want to go back to Windows but It is not looking good.

---

### Post by IWantFroyo on 2011-08-03
Do you mean Ubuntu? I've never heard of an 'Unbuntu'

As for ISO images, you can't load them in WINE. You have to install VirtualBox and follow the Wizards.

As for the .exe files giving you errors in WINE, go over to [www.winehq.org](www.winehq.org) and make sure they're supported. Also, check out the programs' websites to make sure there aren't any native Linux versions.

---

### Post by skatinjj on 2011-08-03
> **IWantFroyo said:**
> 
As for ISO images, you can't load them in WINE. You have to install VirtualBox and follow the Wizards.


virtualbox is for virtualizing other OS on a host, not to read ISO files (OP never said they were ISOs of a OS cd/dvd)

To mount an ISO in linux you would open a terminal and type:

```
sudo mount -o loop /path/to/iso /mnt
```

Now you replace /path/to/iso with the correct directory path and /mnt can be any directory on the system (or you could keep it at /mnt).

---

### Post by skatinjj on 2011-08-03
[http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by cbennett926 on 2011-08-03
Have you given any of the Linux alternatives a try? I have power director my my windows and I am sure there are other video editing and creating files there.

---

### Post by cbennett926 on 2011-08-03
Oops, I mean program.

---

### Post by skatinjj on 2011-08-03
Great place to start when looking for opensource alternatives:

[http://www.osalt.com/]("http://www.osalt.com/")

---

### Post by Mark Phelps on 2011-08-03
> **nortongene said:**
> I just installed Unbuntu and am really happy with it minus I can not load programs I use like Reason, CyberLink Power Director, and other things like that.  I have most of the ISO or exe files and read about using wine.  

Sorry ... but if you have a strong dependency on Windows apps to do stuff on a regular basis, then you really would be better off staying with MS Windows.

Wine is an elegance kludge that works with SOME MS Windows apps, and SOME versions of the same.  Depending on it to do stuff is really a major mistake.  For example, two of the most commonly used MS Windows apps (IE v9 and MS Office 2010) do NOT work in Wine -- at all!  So, if you got used to using them in MS Windows and need to use them in Linux, you're simply out of luck.

You should really look for native Linux apps to take the place of the Windows apps -- but be forewarned, the Linux apps are likely to look a lot different and behave different.

After all, Linux is a free ALTERNATIVE to MS Windows, not a free VERSION of MS Windows.

---

### Post by Furball588 on 2011-08-03
Agreed

I might recommend this guy to ask for a thought on an alternative to Reason

[http://www.jonobacon.org/](http://www.jonobacon.org/)

I know PiTiVi can do video editing, but there is a learning curve (and I don't care for it myself).  Maybe Openshot or VLMC (if you can find a deb or the source) would be decent too..

nortongene:  If you insist on using those, then you'll need to work with the link that skatinjj posted and try to get it working in Wine, which should be available to install through Synaptics (package management).  Sadly apps native to windows won't run without some help in linux, which is where Wine comes into play.  It is an emulator and not everything run with it..but this a considerable amount of success with it.

---

### Post by skatinjj on 2011-08-03
You could virtualize windows in ubuntu but not sure if you could do video editing since I aaume it requires a heavy memory contribution (unless you have a crud ton of memory and processor speed)

---

### Post by scorp123 on 2011-08-03
> **nortongene said:**
> I can not load programs I use like Reason, CyberLink Power Director, and other things like that. **Linux is not Windows!**

Linux distributions such as Ubuntu are a ***different*** OS than Windows and thus have their own native programs for these purposes.

You can't put .45 bullets into a 9mm, you can't fill a diesel vehicle's tank with gasoline (I mean ... you can ... but good luck trying to explain that to your insurance!) and having a driver's license for a car doesn't mean you're qualified to fly a F-22 "Raptor" jet.

So please learn how to do things the "Linux way" ... Insisting on doing things the "Windows way" won't give you the results you expect or hope for.

---

