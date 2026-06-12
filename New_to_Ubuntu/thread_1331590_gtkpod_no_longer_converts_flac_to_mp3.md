---
title: "gtkpod no longer converts flac to mp3"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Charlie Chick on 2009-11-19
Hello Everybody,

After a fresh install of 9.10 my gtkpod has effectively stopped working. Before, I ripped CD's into flac, then dragged & dropped the files into gtkpod. On clicking the save button gtkpod converted the files to mp3.

Now I get an error message: "usr/share/gtkpod-aac/scripts/convert-2mp3.sh-x did not return filename as expected". 

Both LAME and MP3 GAIN are installed. What am I doing wrong?

Thanks,

Charlie

---

### Post by Jon Monreal on 2009-11-19
Try typing into a terminal "sudo apt-get install ubuntu-restricted-extras". This will install MP3 codecs (you should be aware that it installs other proprietary codecs and software as well).

---

### Post by Charlie Chick on 2009-11-20
That was one of the first things that I did after installing!

---

### Post by camaron1 on 2009-11-20
> **Charlie Chick said:**
> Hello Everybody,

After a fresh install of 9.10 my gtkpod has effectively stopped working. Before, I ripped CD's into flac, then dragged & dropped the files into gtkpod. On clicking the save button gtkpod converted the files to mp3.

Now I get an error message: "usr/share/gtkpod-aac/scripts/convert-2mp3.sh-x did not return filename as expected". 

Both LAME and MP3 GAIN are installed. What am I doing wrong?

Thanks,

Charlie

I know it doesn't exactly resolve your problem but you can always use Sounkonverter (with a k). I would not recommend using soundconverter (with a c) because in my experience it just doesn't convert well.

---

### Post by cmege on 2010-03-21
Hi, don't know if this is a the same problem, but I had the same symptoms and solved it by installing flac : sudo apt-get install flac.

---

### Post by plexus on 2010-04-27
worked for me after install lame and flac

```
sudo apt-get install lame flac
```

---

