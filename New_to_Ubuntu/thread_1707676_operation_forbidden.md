---
title: "operation forbidden"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Sina_RJ on 2011-03-15
I want to delete a file but it shows me an error: operation forbidden
what can i do?
i know that the file is a read-only type and i can't even solve this problem too!
can anyone help me?
this file is a virus in my linux-based mobile phone (maemo)

it has to be said,i wanna remove it from my ubuntu maverick meerkat

---

### Post by _0R10N on 2011-03-15
What kind of filesystem it has?

---

### Post by Sina_RJ on 2011-03-15
> **_0R10N said:**
> What kind of filesystem it has?

one of the biggest problems is that!!
this is not a filesystem!
this is a god damn win virus :(
the famous: desktop.ini

---

### Post by grahammechanical on 2011-03-15
I want to make sure that I understand correctly. The file is on your Ubuntu machine. It was transfered from your mobile phone. My guess (and it is only a guess) is that you do not have permission to delete the file because you are not the owner of the file.

My guess is that you need to use the terminal as root and go to the directory/folder where the file is and delete it that way.

Perhaps someone else on the forum could give your the commands to do this.

Regards.

---

### Post by dFlyer on 2011-03-15
Have you tried:

sudo rm -rf filename

---

### Post by Sina_RJ on 2011-03-16
> **dFlyer said:**
> Have you tried:

sudo rm -rf filename

i have to say something,this file is on my mobile phone and i have to browse it with usb or bluetooth
will this command work on that?

the file is on my phone storage
but my phone is based on debian ( maemo 5 )
i have root access on my phone,will this command work there?
i don't have password for phone terminal but i have root access,I have broke the shell for accessing some debian codes!
thanks for help
i'll be happy if you answer this too :)

---

