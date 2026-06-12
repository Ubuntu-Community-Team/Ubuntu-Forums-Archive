---
title: "removing virus"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by user_linux on 2011-08-15
Hi,
MY klam-av has detected a virus and have quarantied it, so how can I remove it? Also, if I want to manually check the file how can I do that? The file path is:
/home/user/.mozilla/firefox/wvjckpy9.default/Cache/177BB111d01
I can't find any file or folder named .mozilla when I start following the path.
Thanks.

---

### Post by whatthefunk on 2011-08-15
The folder .mozilla is a hidden folder. Any folder that begins with a "." is hidden.  Open up a file manager window and hit Ctrl+H to show all files.

---

### Post by mikewhatever on 2011-08-15
```
rm /home/user/.mozilla/firefox/wvjckpy9.default/Cache/177BB111d01
```

..or just clear Firefox cache, but before you do that, does Clam actually say it is a virus? Perhaps it says 'Potentially Unwanted Object' instead?

---

### Post by borderman.badillo on 2011-08-15
there is no such thing as a virus in ubuntu all linux distros have this advantage. just like the mac. the only thing like a virus in ubuntu is the rootkit which damages your file

---

### Post by 3rdalbum on 2011-08-16
If it's in the cache, it's highly unlikely to be a virus. It might just be a Javascript that is noted as being sometimes undesirable - for instance, a Javascript that opens a new window when you close a particular window from your web browser. Some shady websites, such as warez and pr0n, do this. But it doesn't actually cause any harm, it doesn't spread, it's not a virus.

Does Klam actually identify it as a virus? What's the name of the virus?

---

### Post by user_linux on 2011-08-16
Hi everyone,
For clarification, when I ran scan, it showed the file as 1 problems/viruses detected and it said it's probably a virus. The name of the virus found in quarantine is Heuristics.Broken.Executable. So, please advice what should I do?
Thanks.

---

### Post by alexis44 on 2011-08-16
> **user_linux said:**
> Hi everyone,
For clarification, when I ran scan, it showed the file as 1 problems/viruses detected and it said it's probably a virus. The name of the virus found in quarantine is Heuristics.Broken.Executable. So, please advice what should I do?
Thanks.
Have you noticed any problems with your system as a result of this?

---

### Post by whatthefunk on 2011-08-16
This seems like a common problem:
[http://www.google.com/search?hl=en&source=hp&biw=1024&bih=667&q=Heuristics.Broken.Executable&oq=Heuristics.Broken.Executable&aq=f&aqi=g2g-m1&aql=&gs_sm=e&gs_upl=3820l3820l0l4386l1l1l0l0l0l0l409l409l4-1l1l0](http://www.google.com/search?hl=en&source=hp&biw=1024&bih=667&q=Heuristics.Broken.Executable&oq=Heuristics.Broken.Executable&aq=f&aqi=g2g-m1&aql=&gs_sm=e&gs_upl=3820l3820l0l4386l1l1l0l0l0l0l409l409l4-1l1l0)

Do you run .exe files in Wine?

---

### Post by user_linux on 2011-08-16
No but I just feel if it's a virus, then it should be removed, shouldn't it for your system safety?

---

### Post by user_linux on 2011-08-16
No, I don't run any .exe file in a Wine prog.
> **whatthefunk said:**
> This seems like a common problem:
[http://www.google.com/search?hl=en&source=hp&biw=1024&bih=667&q=Heuristics.Broken.Executable&oq=Heuristics.Broken.Executable&aq=f&aqi=g2g-m1&aql=&gs_sm=e&gs_upl=3820l3820l0l4386l1l1l0l0l0l0l409l409l4-1l1l0](http://www.google.com/search?hl=en&source=hp&biw=1024&bih=667&q=Heuristics.Broken.Executable&oq=Heuristics.Broken.Executable&aq=f&aqi=g2g-m1&aql=&gs_sm=e&gs_upl=3820l3820l0l4386l1l1l0l0l0l0l409l409l4-1l1l0)

Do you run .exe files in Wine?

---

### Post by user_linux on 2011-08-16
No but I just feel if it's a virus, then it should be removed, shouldn't it for your system safety?
> **alexis44 said:**
> Have you noticed any problems with your system as a result of this?

---

### Post by scottishbloke on 2011-08-16
Its not a virus, Ignore It and relax.

---

### Post by Johnb0y on 2011-08-16
> **scottishbloke said:**
> Its not a virus, Ignore It and relax.

+1

Chill! lol!

---

### Post by beew on 2011-08-16
I think a lesson to be learned is that  ClamAV is probably useless.

---

### Post by Johnb0y on 2011-08-16
> **beew said:**
> I think a lesson to be learned is that  ClamAV is probably useless.

like a lot of "anti"-virus software out there... some dont even "find" the obvi... one reason why i ditched windows...

---

