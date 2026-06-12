---
title: "text editor"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by LadyA on 2010-07-17
My gedit text editor has been working perfectly until today. Now it fails to print. I use it all the time and would like to get it fixed.

---

### Post by d3ngar on 2010-07-17
Hey LadyA,

I somehow wonder if it's gedit that causes you trouble when printing...

I thought you should be able to run it in debug mode, but that doesn't seem to be an option. Have you tried to completely remove it and then install it again?

```
 XX@XX$ sudo apt-get purge gedit
XX@XX$ sudo apt-get install gedit 
```

You could also try to reconfigure it:

```
XX@XX$ sudo depkg-reconfigure gedit 
```

---

### Post by mike555 on 2010-07-17
If you can't get gedit working you might try "Scribes " it is the only auto-saving text editor I have found (I did change the default theme though )

---

### Post by Morbius1 on 2010-07-17
Is CUPS running?

```
sudo service cups status
```If it's not - start it:
```
sudo service cups restart
```
Of course if it's not running then it would impact printing from everything.

---

### Post by LadyA on 2010-07-17
d3ngar, I tried, in terminal, Sudo depkg-reconfigure gedit and it said command not found.
Morbius1, my service cups is running. I can print from open office.
mike 555, I downloaded scribes and I couldn't print from it because the print icon was grayed out, so how do you print from it.
I would  like my gedit to be fixed because I really like that text editor.

---

### Post by techunit on 2010-07-17
> **LadyA said:**
> d3ngar, I tried, in terminal, Sudo depkg-reconfigure gedit and it said command not found.
Morbius1, my service cups is running. I can print from open office.
mike 555, I downloaded scribes and I couldn't print from it because the print icon was grayed out, so how do you print from it.
I would  like my gedit to be fixed because I really like that text editor.

That is a typo....

the code you need is 

```
sudo dpkg-reconfigure gedit
```

---

### Post by LadyA on 2010-07-17
techunit, I fixed the typo and it came back with 
[update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto mode].
What does this mean? I don't know too much about using the terminal.

---

### Post by mike555 on 2010-07-17
Never noticed that grayed out print (in Scribes) ,it appears that you printer must be on and connected before opening scribes , otherwise you need to reopen it , then the print should show (it does on mine).

---

### Post by Morbius1 on 2010-07-17
> update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto modeOn my system ( I can print from gedit ):

/usr/bin/gnome-text-editor is a symlink to /etc/alternatives/gnome-text-editor
/etc/alternatives/gnome-text-editor is a symlink to /usr/bin/gedit

I think the message you got was simply a statement of fact.

Doesn't get us any closer to determining why you can't print from gedit.

---

### Post by LadyA on 2010-07-17
I have tested the printer on webpages, open office, etc and the only place it doesn't work is gedit editor.
Also, mike555, I made sure the printer was turned when I launched Scribes and the printer icon was still grayed out. I must be having a bad day.

---

### Post by techunit on 2010-07-18
Hi sorry for the delay for my reply... I am not sure why it isn't working... I really want to help but when they posted the typo I was really just trying to make sure you could try that.. 

here could you try this...

```
sudo aptitude purge gedit

sudo apt-get autoremove

sudo apt-get autoclean

apt-get install gedit
```I hope this helps... this should completely remove gedit and reinstall it...

If this doesn't work take a look at leafpad it is a nonsyntax text editor

```
sudo apt-get install leafpad
```

Note if you are just using gedit for a list making software I.E. shopping list you should look at tomboy notes (preinstalled)

---

