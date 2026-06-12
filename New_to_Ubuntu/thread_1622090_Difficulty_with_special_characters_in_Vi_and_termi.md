---
title: "Difficulty with special characters in Vi and terminal"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by adam s on 2010-11-15
I am trying to run the command 

:%s/,/^M/g

which obviously should replace any comma with a carriage return

BUT I run multiple languages on my system and so when I press the CTRL-V to include a special character I get a different letter rather that the option to include a special character.

Any ideas how to get round this (without removing my multiple keyboard layouts).

Thanks in advance,

Adam.

---

### Post by robsoles on 2010-11-15
[s]Can you right click and choose paste?[/s]

Sorry, stupid question - ouch VI - bit me once, can you use nano?

---

### Post by bioterror on 2010-11-15
> **adam s said:**
> I am trying to run the command 

:s/,/^M/g

which obviously should replace any comma with a carriage return

BUT I run multiple languages on my system and so when I press the CTRL-V to include a special character I get a different letter rather that the option to include a special character.

Any ideas how to get round this (without removing my multiple keyboard layouts).

Thanks in advance,

Adam.

Should you use shift+insert instead to paste or mouse middle button?

```
:%s/word/to_new_word/g
```

And that's how I do it.

---

### Post by adam s on 2010-11-15
Hi,

robsoles - Nano requires CTRTL characters which is the exact problem that I have as I needt to do a CTRL V command - therefore this doesn't work

Bioterror - I can paste using CTRL SHIFT V but I need to be able to use the CTRL characters. I need to somehow turn off the multi-charar=cter set option that allows the system to switch temporarily between char sets when holding down the CTRL button.

Thanks,

Adam.

---

### Post by bioterror on 2010-11-15
I think vi/vim does not support these ctrl-ansi codes, or what are those called.

---

### Post by adam s on 2010-11-15
It is standard practice in the command mode of Vi (at least on UNIX) if you wish to put in characters like an escape key, or enter or home  key etc to do a CTRL-V followed by the key press.

I remember (although I could be wrong) doing this in ubuntu in the old days before I used multiple character sets. Unfortunately the multiple character sets seems to stop this working.

Thanks,

Adam.

---

### Post by adam s on 2010-11-15
Partially solved.

I opened the file in gedit put in my own CR copied this and then pasted the result in the replace box.

Although this solves my current problem, it still doesnt allow me to include key presses in vi or other terminal programs.

Any other ideas?

Thanks,

Adam.

---

### Post by bioterror on 2010-11-15
first you press "i" like insert, then you ^V and right after that ^M

I managed to make colors with ^C

---

### Post by adam s on 2010-11-15
Still doesn't work.

The problem is that the functionality of the CTRL button has been changed due to the multiple character sets.

Adam.

---

### Post by benson444 on 2010-11-15
The file /usr/share/vim/vim72/doc/usr_40.txt has info about key mapping. I can't remember how to read the user-manual files from within vim, so I just cat-ted it.

:imap <F2> <C-V>

I think that's what you mean, but don't know if it works the same way in vi and vim.

Edit:
Sorry, you need to map the key in command mode, not insert mode, so need

:cmap <F2> <C-V>

---

### Post by adam s on 2010-11-15
Same problem I can't do ctrl V it comes out as &#1492;

Adam.

---

### Post by benson444 on 2010-11-15
Do you mean that you still get that character when you press F2 after mapping it to Ctrl-V?

Edit:
I guess you do. I don't know why I thought that might work really as it's obviously using the mapping to just call Ctrl-V rather than using it as any kind of alternative. Oh well.

---

### Post by jwbrase on 2010-11-15
Does using the other Ctrl key help?

Does going to System -> Preferences -> Keyboard, then to the "Layouts" tab and hitting the "Options" button and selecting something like "Alt + Capslock" under "key(s) to change layout" help? (Note, you'll also have to deselect the Ctrl key, since it allows you to have multiple options selected).

---

### Post by adam s on 2010-11-16
Unfortunately neither of the CTRL keys work and the "keys to change layout" to ALT plus CTRL also didn't work.

Thanks,

Adam.

---

### Post by adam s on 2010-12-06
Hi,

Thanks for all the help. I have solved it by using vi in xterm. It seems to be a "system feature" of the terminal when using multiple keyboard layouts.

Thank for all the help,

Adam.

---

