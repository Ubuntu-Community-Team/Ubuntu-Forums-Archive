---
title: "[SOLVED] how to quit editing and go back to cli?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-11
How do I get back to cli when editing a file?

---

### Post by rakris on 2008-12-11
you mean when using vim? esc+:q

Or you mean when using desktop? alt+F1 ..

Dont know what u asked

---

### Post by pshootr on 2008-12-11
I am running ubuntu server 8.10 And when I am editing a file, I dont know how to exit if you will, and get back to the CLI

---

### Post by nhasian on 2008-12-11
I hope your talking about vi(m) because it rules ):P

it has a rather steep learning curve but i found the vim-tutor very helpful.  its not installed by default so you need to do:

```
sudo apt-get install vim-full
```

then you can start the tutor with:

```
vimtutor
```

cheers

---

### Post by Michael.Godawski on 2008-12-11
What command are you using to edit the file?
for vi it is esc and
```
:q
```
enter

---

### Post by pshootr on 2008-12-11
> **Michael.Godawski said:**
> What command are you using to edit the file?
for vi it is esc and
```
:q
```
enter

/etc/network/interfaces    That is how I opened the file

---

### Post by Kobalt on 2008-12-11
That doens't tell us which file editor you use : which command exactly did you enter?

---

### Post by pshootr on 2008-12-11
> **Kobalt said:**
> That doens't tell us which file editor you use : which command exactly did you enter?

I'm not using any editor per say. I am just booting as root in to ubuntu server with just a command line interface. Should I type in a command to get to the editor? I was just typing "/etc/network/interfaces" in the command line. Sorry for my newbness

---

### Post by nhasian on 2008-12-11
that path leads to a file but to edit it you need to use a program like vi or nano with sudo.

```
sudo vi /etc/network/interfaces
```

```
sudo nano /etc/network/interfaces
```

if you just want to see what the file contains you can just use cat.

```
cat /etc/network/interfaces
```

---

### Post by pshootr on 2008-12-11
> **nhasian said:**
> that path leads to a file but to edit it you need to use a program like vi or nano with sudo.

```
sudo vi /etc/network/interfaces
```

```
sudo nano /etc/network/interfaces
```

if you just want to see what the file contains you can just use cat.

```
cat /etc/network/interfaces
```

Ok cool. Thank you very much. So when I use vi, how will I save and exit? or exit without saving?

---

### Post by prshah on 2008-12-11
> **pshootr said:**
> So when I use vi, how will I save and exit? or exit without saving?

save & exit```
[ESC]:wq
``` exit without saving```
[ESC]:q!
```

== OR if you decide to use nano:

Ctrl+O = Save (writeOut)
Ctrl+X = Exit (eXit)

If you press Ctrl+X you will be prompted to save the changes, if any;  you can choose to exit without saving or save and then exit. If you choose to save the file, you will be prompted for a new filename; if you want to use the same filename, just press enter; otherwise, type the (full path) new file name.

---

### Post by rakris on 2008-12-11
```
:wq or :q
```

---

### Post by oldos2er on 2008-12-11
"So when I use vi, how will I save and exit? or exit without saving?"

 nano is a much simpler text editor, assuming you've never used vi(m).

---

### Post by decoherence on 2008-12-11
A couple of things I've seen bite nano newbs ;)

Pressing CTRL S to save will result in a cryptic and mildly amusing message (and will not save)

Pressing CTRL Z will not undo. If you type CTRL Z out of habit, you can get back to the editor by typing the command "fg" (CTRL Z stops a program, which is different from quitting it in that you can resume where you left off... that's what the "fg" or 'foreground' command is for)

---

### Post by EmanresuusernamE on 2008-12-11
IMO, until vi or vim get some kind of TUI like pico/nano, I'll still choose pico/nano over them.  I like the fact that I didn't have to learn a whole new set of commands through trial and error (I had people telling me what to do when I first used it, when they weren't there I forgot the commands) there to be able to save and quit.  I just looked at the bottom and did as it says.  I won't deny that vi(m) is powerful in the least bit, but when I want to edit text, I just want to edit it and be done with it.

---

### Post by pmains on 2008-12-11
As pointed out above, VI has a steep learning curve. It's not all that difficult, but finding a good introduction would be good.

i -- go into insert mode, starting before current character.
a -- go into append mode, starting after current character.
o -- start a new line and enter insert mode.
esc -- exit insert mode.
/abc -- search for "abc"
:%s/abc/123/g -- replace instances of "abc" with "123"
:3,5s/abc/123/g -- replace instances of "abc" with "123" on lines 3 to 5
yy -- yank (copy) current line
y$ -- yank everything from current char to the end of the line
dd -- delete and copy current line
p -- paste yanked/deleted text after current character
P -- paste yanked/deleted text before current character
h,j,k,l -- left, up, down, right

---

