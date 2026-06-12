---
title: "Help me!! Help ME!!"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by request_another on 2010-05-11
I broke the terminal! I was looking at this thread 

[http://ubuntuforums.org/showthread.php?t=1090294&page=3](http://ubuntuforums.org/showthread.php?t=1090294&page=3)

where i typed in "gedit .bashrc". From here i added the line from post number 24. This is supposed to show me quotes from futarama every time i open the terminal but since i didnt have curl installed to begin with every time i launch the terminal it say i need to install curl and i cant do anything then

[img]http://img691.imageshack.us/img691/2716/screenshot1jk.png[/img]

Whtever i type from here nothing happens, it just goes onto the next line.I figured i need to go back to the bashrc file and edit it but apparently the file is in my root folder which i cant access without su. Or i could install curl and sort this but i cant install it without the terminal!

---

### Post by request_another on 2010-05-11
ok i think i sorted it! phew! I checked ubuntu software center for curl and it was there.

---

### Post by bapoumba on 2010-05-11
You could go to one of the vt (ctrl-alt-F2 for ex) and install said package with sudo apt-get install curl. Then go back to your graphics session (ctrl-alt-F7).

Edit: Meh, was too late and too slow again :D

---

### Post by request_another on 2010-05-11
oh no, i  think i broke it again. I pasted 

cowsay -f bender $(curl -Is slashdot.org | egrep '^X-(B)' | cut -d \- -f 2)

into the bashrc, which i got from the same  thread, but now nothing at all happens at the terminal. Is there a way i can get into the bashrc file and edit it?

---

### Post by request_another on 2010-05-11
ok false alarm. after opening the terminal a few more times it loaded up. It seems it wasnt communicating with the server well because it tries to get the quotes online i think.

---

### Post by mhgsys on 2010-05-11
You've just stole my precious time

---

### Post by request_another on 2010-05-11
sorry :P

---

### Post by mhgsys on 2010-05-11
> **wankingweiner said:**
> sorry :P

I forgive you..




just for using ubuntu

---

### Post by Merk42 on 2010-05-11
Please go to Thread Tools and click "Mark this thread as solved"

---

### Post by mhgsys on 2010-05-11
> **Merk42 said:**
> Please go to Thread Tools and click "Mark this thread as solved"


You know; That would be an excellent idea; 

You should do that; while I get my subscription off this thread; 
Actually I was watching something, and I got the email containing the great idea of merk42

---

### Post by request_another on 2010-05-11
> **Merk42 said:**
> Please go to Thread Tools and click "Mark this thread as solved"

alright done

---

