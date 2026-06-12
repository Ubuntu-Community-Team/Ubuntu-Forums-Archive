---
title: "Chromium and backspace"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-10-03
since when has backspace been able to navigate rather than delete mistakes?  Anyone know how to turn that bloody annoying feature off?

---

### Post by johny_ on 2009-10-03
You mean you can't delete any text with it?

---

### Post by baltadt on 2009-10-03
backspace works just fine for me. Need a little more info on what you were doing.

---

### Post by themusicalduck on 2009-10-03
I had this today and it was really annoying. Although I just now did an update and it's been fixed.

---

### Post by Dobbie03 on 2009-10-03
Correct, it navigates back to the previous page instead.  It only started happening after todays installation of the latest nightly build.  Hopefully it will correct itself.

---

### Post by vickoxy on 2009-10-03
Hi-just installed Chromium 4.0.221.1 (Ubuntu build 27838 ) and have the same issue-please if someone find solution.

---

### Post by Dobbie03 on 2009-10-03
> **vickoxy said:**
> Hi-just installed Chromium 4.0.221.1 (Ubuntu build 27838 ) and have the same issue-please if someone find solution.

Same build as mine, it will most probably fix itself with the next build, well at least thats what I am hoping.

---

### Post by vickoxy on 2009-10-03
Just made update to 4.0.221.3 (Ubuntu build 27948 ), and it is fixed. 

Well, they are fast...

---

### Post by Dobbie03 on 2009-10-03
Did you update via Update Manager?

---

### Post by vickoxy on 2009-10-03
Synaptic, yes-just reload and installed update

---

### Post by vickoxy on 2009-10-03
I added it in synaptic: [http://ubuntuforums.org/showthread.php?p=8011072](http://ubuntuforums.org/showthread.php?p=8011072)

Did you have fixed it?

---

### Post by Dobbie03 on 2009-10-03
Damn it I cant get it to update.

---

### Post by Dobbie03 on 2009-10-03
I tried updating with 

sudo apt-get update chromium-browser

but that didnt work.

---

### Post by vickoxy on 2009-10-03
You have it in repos /source list/? If so, just open synaptic, press reload, than press install updates, and it should be shown google-chromium.

---

### Post by Dobbie03 on 2009-10-03
Yes it is in my repos, it just won't recognise that Chromium has an update available.  I am getting a touch annoyed by all of this.

---

### Post by Dobbie03 on 2009-10-03
I upgraded to the latest build, still having the same issue of backspace navigating to the previous page.

---

### Post by vickoxy on 2009-10-03
> **MattDobson said:**
> Yes it is in my repos, it just won't recognise that Chromium has an update available.  I am getting a touch annoyed by all of this.

Well, i do not know how is that possible-i just pressed reload, then pressed next button there (something like-selct updates) and after that the third button-install-and just then it shows chromium update

---

### Post by hhhealthy on 2009-10-03
I had the same issue. and hopefully i can help some.

i originally found what sources to add from a specific website.

[http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/](http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/)

i didn't notice right away that they were from intrepid and not jaunty.

i found this thread trying to figure out how to fix my backspace issue and followed the link at top to the other how-to.

[http://ubuntuforums.org/showthread.php?p=8011072](http://ubuntuforums.org/showthread.php?p=8011072)

noticed that that one added the unbuntu jaunty main and after looking back realized that it was intrepid on the other. 

anyway long story story short, i wasn't getting the newest update when i was checking the intrepid source. i changed my source.list to the jaunty one and it found the newer upgrade. i did

```
sudo apt-get update
```

```
sudo apt-get upgrade -u
```

and you should see chromium come up in that. hit y and it worked for me. good luck.

---

### Post by Dobbie03 on 2009-10-03
> **hhhealthy said:**
> I had the same issue. and hopefully i can help some.

i originally found what sources to add from a specific website.

[http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/](http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/)

i didn't notice right away that they were from intrepid and not jaunty.

i found this thread trying to figure out how to fix my backspace issue and followed the link at top to the other how-to.

[http://ubuntuforums.org/showthread.php?p=8011072](http://ubuntuforums.org/showthread.php?p=8011072)

noticed that that one added the unbuntu jaunty main and after looking back realized that it was intrepid on the other. 

anyway long story story short, i wasn't getting the newest update when i was checking the intrepid source. i changed my source.list to the jaunty one and it found the newer upgrade. i did

```
sudo apt-get update
```

```
sudo apt-get upgrade -u
```

and you should see chromium come up in that. hit y and it worked for me. good luck.

Sweet, thanks that worked.

unfortunately I am still having the same issue with the backspace key.

---

### Post by vickoxy on 2009-10-03
Try to log out and log in/restart.

You do have this build: 4.0.221.3 /Ubuntu build 27948/?

---

### Post by STop on 2009-10-03
I can confirm that build 4.0.221.3 solved the backspace issue.
And as vickoxy wrote, you need to log out and back after updating.

BTW, I had the same issue in Midori (also Webkit based) on my netbook running Kuki Linux (an Ubuntu derivative). But Midori allows reconfiguring keybindings...

---

### Post by Dobbie03 on 2009-10-03
I better do that then.

Thanks everyone.

---

