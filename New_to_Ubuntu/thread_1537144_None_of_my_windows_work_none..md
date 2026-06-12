---
title: "None of my windows work none."
date: 2010-07-23
forum: New to Ubuntu
---

### Post by leon951 on 2010-07-23
Hello i have a problem (i run ubuntu 10.4) right after i instald "ftk-record my desktop" the optional buttons wouldnt apear. You know the good old "^" to maximize the widnow or to minimize it and to close it (as you can see in my firefox web widnow). they are gone i might've goten a corupdted scripd.... allready unistald it but it didnt change back to normal. (pleas forgive my spelling)[IMG]http://i948.photobucket.com/albums/ad328/leon951/Screenshot.png

---

### Post by pushkarajthorat on 2010-07-23
this happend with me too, when i was on gnome, but once i did relogin, everything worked fine. Also try stopping compiz(by right click on desktop, properties, and turn off the compiz)

---

### Post by int2ag0n on 2010-07-23
Try this ->
Open "Run Application" (alt+F2) and
if you use compiz write :
      compiz-decorator --replace

if you use metacity (no compiz) write:
      metacity-decorator --replace

Don't forget to hit Enter!

---

### Post by leon951 on 2010-07-23
thank [pushkarajthorat]("http://ubuntuforums.org/member.php?u=686162"), i tryd restaring the computer bout 4 times and nothing changed but for some reason it workd after i turnd it off for bout 6 hours.

---

### Post by leon951 on 2010-07-23
Thank you [int2ag0n]("http://ubuntuforums.org/member.php?u=727865") it happen once again and your code worked great. any hints what program i should use to stop this from happening?

---

### Post by int2ag0n on 2010-07-24
The windows decorator is missing every time you login or randomly?
I don't know exactly what's wrong , but i will search for it and i'll let you know.

---

### Post by int2ag0n on 2010-07-24
Leon951 ,if you are using Compiz try this , open CompizConfig Settings Manager and check if the Window Decorator box is enabled , and also check in the General tab the Command value . Mine is gtk-window-decorator --replace because i use gnome.

---

