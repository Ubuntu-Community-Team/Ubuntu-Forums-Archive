---
title: "What is the default font path?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by dberebi on 2009-03-09
I'm developing a php script that will use font files to write on images (with GD), I want the script to guess the right font path, so the user should only set the font name.

On windows it's usually 'C:\Windows\Fonts'

I've searched the net and found these but I can't test them since my host doesn't allow me to read them:
		/usr/share/fonts/local/
		/usr/share/X11/fonts/
		/usr/X11R6/lib/X11/fonts/
		/usr/share/fonts/
		~/.fonts 

If it's matter, I'll use only TrueType or FreeType fonts.

What is the best guess? is there a way to get it somehow?

Thanks for helping! :D

---

### Post by albandy on 2009-03-09
/usr/share/fonts/truetype/thefontpackyouwanttouse

for example, if you want to use windows fonts do
sudo apt-get install msttcorefonts
then this folder will appear
/usr/share/fonts/truetype/msttcorefonts

---

### Post by dberebi on 2009-03-09
But from php usually the user can't use 'apt-get' nor 'sudo', nothing...

That is the reason I'm searching for a **default** path,
Is there any default pack inside '/usr/share/fonts/truetype/' ?

Thanks again for your help :thumbs up:

---

### Post by albandy on 2009-03-09
where are you running your php?

---

### Post by dberebi on 2009-03-09
Currently on windows, but I want to make a class that will work as best as possible on every server

---

### Post by albandy on 2009-03-09
you can't, every linux distro works different, and servers will use any kind of o.s. like solaris, freebsd, linux, ....

So I recomend you to use a config file for you class allowing user to specify the folder where fonts are stored.

Also a well configured server will not let you acces to it's folders, only to the web folder.

---

### Post by dberebi on 2009-03-09
well, I guess you right :(

Thanks :)

---

