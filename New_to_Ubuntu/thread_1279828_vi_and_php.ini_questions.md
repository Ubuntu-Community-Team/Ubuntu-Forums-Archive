---
title: "vi and php.ini questions"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by melbs on 2009-10-01
I am trying to edit the php.ini on ubuntu 8.04 with vi/vim. I have a few questions:

- If I do vi filename or vim filename is it the same program?

- I exited out of php.ini because I didn't want to screw anything up and some wierd characters were entered accidently, it created a swp file. Where is this file for me to delete it? It's not in that directory.

-When I use vi filename and hit "i" to start editing, I hit the arrow and it produces a "C" and "D". I also have problems with hitting ESC to exit the insert mode.

-Can I cp php.ini php2.ini to create a backup of the php.ini file to be safe?

I'm just starting up again with working with command line and I was a newbie to begin with. Any help on my above issues would be greatly appreciated! Thank you!

---

### Post by credobyte on 2009-10-01
File backups usually contain tilde ( ~ ) - as an example, php.ini~.

---

### Post by melbs on 2009-10-01
So when I do the cp php.ini php.ini~ ... do that?


Also, I am working with Moodle I changed settings in php.ini to increase file upload sizes. Do I have to restart apache or anything for them to take affect? It doesn't seem to have worked (if I did it right).

---

### Post by credobyte on 2009-10-01
> **melbs said:**
> So when I do the cp php.ini php.ini~ ... do that?
Yes.

> **melbs said:**
> Also, I am working with Moodle I changed settings in php.ini to increase file upload sizes. Do I have to restart apache or anything for them to take affect? It doesn't seem to have worked (if I did it right).
Yes.

---

### Post by allenbradley on 2009-10-01
vi has a couple of funny quirks. The navigation (when not in insert mode ) is using the hjkl keys, so vi phreaks out when you use arrow keys.
Solution? Use vim.
vim is vi-improved, so it fixes this little thing ( though some might agree iots not a fix ) A nice thing to try out would be to try vimtutor.
```
vimtutor
```
It's a really nice tutorial on vim. For further info, use the vim wiki :[HTML]http://vim.wikia.com/wiki/Vim_Tips_Wiki[/HTML]
Hope that helps.

---

### Post by jonobr on 2009-10-01
Showing my age here,
in older systems when vi started up first,
the keys hjkl had arrows on them.

Then came keyboards with dedicated arrows, however, people were used to hjkl so it stuck..

---

### Post by melbs on 2009-10-01
Great! Thanks!

And do you or does anyone know where the php.ini.swp file is which was made when I exited out unconventionally? I need to delete that so I don't get the warning again.

---

### Post by melbs on 2009-10-01
Wow thanks for the info on vi/vim guys! That must be what I was running into with he arrows.

Quick question, if I ever use the arrows and it produces C, D.. how can I cleanly exit from vi? Before I just Xd the window out of putty! I plan to use vim but just wondering. Thanks!

---

### Post by jonobr on 2009-10-01
Hello


With vi


hit esc to go into command mode and then 

```
:q!
```

To quit without saving changes

using a w with q! will write and quit but you need the one above

---

### Post by melbs on 2009-10-08
I'm still trying to figure out where that php.ini.swp file is and how to delete it? Thanks.

---NEVERMIND got it : )


But another question. I edited the php.ini to change the upload size for Moodle, the software I'm working with. I changed it, restarted and it does not seem to be taking effect. I also tried using an .htaccess file, which also did not work.


How do I know I'm working with the right php.ini file - is there more than one? And where is the Apache server setting LimitRequestBody, which file? Thanks!

---

### Post by wojox on 2009-10-08
Try and open a terminal:

```
locate php.ini.swp
```

Then:

```
sudo rm /path/to/file/php.ini.swp
```

---

