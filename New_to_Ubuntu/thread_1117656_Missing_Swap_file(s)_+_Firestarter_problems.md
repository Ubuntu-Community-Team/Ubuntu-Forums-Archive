---
title: "Missing Swap file(s) + Firestarter problems"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Sir Jasper on 2009-04-06
Hi,

I had a dual boot 8.10 and W98SE.
I used to only see the Ubuntu logo when booting Ubuntu

I now have triple boot 8.10 (two separate versions) and W98SE
I now see details of the boot loading with both 8.10 versions
On the old version of 8.10 the Firewall should be operaional
I have not set up a Firewall on the latest version.


The above is a only a brief summary since queries are general:

(1) When I boot into my old 8.10 there is a red [fail] for Firestarter
but when I load Firestarter it says Active and all appears to be well.
I set up boot logs and \var\boot\log exists but nothing is recorded there, so it is difficult to give more detail. 

(2) Both versions of 8.10 appear not to have an Active Swap file.
I tried test-loading far more concurrent programs than I would ever use ordinarily but nothing seemed to slow and there was no crash or lock-up. 

Should I investigate more now (not so easy with my limited proficiency) or will it probably be OK to defer that unless and until any obvious problem(s) may occur?

My regards

---

### Post by gn2 on 2009-04-06
Firestarter is a GUI for changing firewall settings.
You don't need to have it running, many believe it's better not to have it running.

Reading [this]("http://ubuntuforums.org/showthread.php?t=510812") might be useful.

---

### Post by Sir Jasper on 2009-04-06
Hi Gn2,

Thank you for the helpful link. It seems to me (perhaps mistakenly) that if (once the firewall is set up) is not necessary for Firestarter to be active, then couldn´t I just uninstall Firestarter?

Hi all,

If the above is true, and it is harmless to uninstall Firestarter because the Firewall will remain active - that would only leave the Swap file question.

My regards

---

### Post by gn2 on 2009-04-06
No need to uninstall Firestarter, just set it so that it doesn't start at boot.
You can uninstall it if you wish.

A default Ubuntu installation doesn't hav a swap file, it has a swap partition.

System > Administration > System Monitor > Resources will show you how much swap is in use.

---

### Post by Sir Jasper on 2009-04-06
Hi gn2,

Thank you for your help.

I have uninstalled Firestarter which now eliminates the red [fail] message when loading.

I have now temporarily deleted the Swap partition as although I only have 640 MB RAM (565 MB available) just to test since Swap never seems to get used.

My regards

---

