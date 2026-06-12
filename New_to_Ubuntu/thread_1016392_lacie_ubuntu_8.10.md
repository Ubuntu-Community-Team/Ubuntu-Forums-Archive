---
title: "lacie ubuntu 8.10"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by ken095 on 2008-12-19
I have successfully converted the rpm to an deb file and have lacie lightscribe lableler working ok the problem is after I tell it to print the disk it comes back with "printing requires root priviliges" any help would be great.

Ken095

AMD-64-3500 Ubuntu Ultimate 8.10 1.5ram liteon dvdrw shm-165h6s

---

### Post by nordmichael29 on 2008-12-19
if it's on a command line just type in sudo and then the command(s) you want to use.
if not I thin you have to give the program root privilages (I don't knwo how to do that, I'm afraid I'm a bit of a noob)

---

### Post by rotwang888 on 2008-12-19
Try opening a terminal and running the program with "gksudo" plus the name of the program. I assume lacie?  So it would be "gksudo lacie". It will ask for your passwork and then open. This will run the program as root.  If the name isn't exactly lacie, you can enter the first couple letters and hit tab, which will auto-complete the entry.
 Edit: gksudo would be to run a program with a graphical interface.  If it's not, do as nordmichael29 says above.

---

### Post by ken095 on 2008-12-19
I would love to do it in gui if possible

Ken095

---

### Post by nordmichael29 on 2008-12-19
ah really? that's sweet rotwang, can you do this from the alt+f2 run program thing?

---

### Post by ken095 on 2008-12-19
didnt work  ??

Ken

---

### Post by rotwang888 on 2008-12-19
> **nordmichael29 said:**
>  can you do this from the alt+f2 run program thing?

 I don't think so.  As far as I know you have to use the terminal.  A handy use of this is to run "gksudo nautilus" if you're trying to move files in the gui and running into permission errors.

---

### Post by rotwang888 on 2008-12-19
> **ken095 said:**
> didnt work  ??

Ken

 How were you running the program the first time when it gave you the root message?

---

### Post by ken095 on 2008-12-19
ya

---

### Post by rotwang888 on 2008-12-19
> **nordmichael29 said:**
> can you do this from the alt+f2 run program thing?

 Or did you mean the auto-complete thing?  That DOES work with alt+f2.

---

### Post by ken095 on 2008-12-19
loaded it into the menu and clicked it it ran fine but it just wants permission to print

Ken

---

### Post by ken095 on 2008-12-19
I loaded it up in the menu and it ran fine it just wants permission to print

Ken

---

### Post by ken095 on 2008-12-19
no auto complete

---

### Post by ken095 on 2008-12-19
gg thanks fer the help

Ken

---

### Post by rotwang888 on 2008-12-19
> **ken095 said:**
> ya

 I mean when you ran the program before, did you enter a command in a terminal, or click an icon in the applications menu, or something else?

---

### Post by nordmichael29 on 2008-12-19
> **rotwang888 said:**
> Or did you mean the auto-complete thing?  That DOES work with alt+f2.

I was meaning the gksudo and then program name to run as root, thanks for helping I'm sure I'll use that soon if not tonight =)

---

### Post by SunnyRabbiera on 2008-12-19
> **ken095 said:**
> I would love to do it in gui if possible

Ken095

Sometimes you have to live with the terminal in linux, as some applicarions and junk dont have a gui... yet.

---

### Post by rotwang888 on 2008-12-19
You need to know the name of the command that starts the program.  It's usually just the name, like firefox, but I'm not sure what the "real" name of the program you're running is.  To find out for sure, right-click on applications and click "edit menus".  Click the category it's in on the right, and the icon for the program itself in the center, and click "properties" on the right.  Look for the text under "command" in the window that comes up.  That is what you have to run with "gksudo name-of-command".

---

