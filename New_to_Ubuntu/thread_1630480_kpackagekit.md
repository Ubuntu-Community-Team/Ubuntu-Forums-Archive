---
title: "kpackagekit"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by beew on 2010-11-25
Hi,

I just started playing around with KDE so this may be a very dumb question. How do you find all the installed programs in kpackagekit? Are there search and browse functions by status (all installed, not installed etc)similar to Synaptic or do you need to know the exact name of a package to locate it? If it is the latter is there anything similar to Synaptic in KDE?

---

### Post by QLee on 2010-11-25
[QUOTE=beew]
I just started playing around with KDE so this may be a very dumb question. How do you find all the installed programs in kpackagekit? Are there search and browse functions by status (all installed, not installed etc)similar to Synaptic or do you need to know the exact name of a package to locate it? If it is the latter is there anything similar to Synaptic in KDE?[/QUOTE]

I can't answer your actual question, beew, because I don't use KDE but it is possible to use synaptic in that environment. Probably would pull in some dependencies though and if you're trying to keep a "pure" system you might not want that.

I know from our previous discussion that you don't like a command line approach but see if, 
dpkg --get-selections | less, in a terminal window gives what you are looking for. I've piped the output from dpkg through "less" to allow you to read them all on the terminal, you could also output to a file.

---

### Post by oldos2er on 2010-11-25
Filters, Installed, Only Installed.

---

### Post by beew on 2010-11-26
> **QLee said:**
> I can't answer your actual question, beew, because I don't use KDE but it is possible to use synaptic in that environment. Probably would pull in some dependencies though and if you're trying to keep a "pure" system you might not want that.

I know from our previous discussion that you don't like a command line approach but see if, 
dpkg --get-selections | less, in a terminal window gives what you are looking for. I've piped the output from dpkg through "less" to allow you to read them all on the terminal, you could also output to a file.


Hi,

It is not that I don't like the command line approach, I just don't like people abusing it :)
The point I made was that if you try to explain something to a beginner throwing a bunch of cryptic looking gibberish at him/her and tell him/her to cut and paste doesn't really contribute to learning, whereas the gui, while probably not up to the task for something complex, but at least the user can intuit the logic.

I know the dpkg -l | less command except there is an added complication. This is actually a Fedora installation (actually not quite, it is a Chinese distro called qomo which is very similar to Fedora and uses KDE, I am setting it up for a friend who definitely doesn't like command lines. :) ) dpkg is a Debian thing so it wouldn't work.

Thanks for the response though.

---

### Post by beew on 2010-11-26
> **oldos2er said:**
> Filters, Installed, Only Installed.

I may be missing something but I don't think that would do what I want. If I am not mistaken setting the filter options the way you said only limits the search to installed software, but it wouldn't display all the display softwares like Synaptic does.

---

### Post by QLee on 2010-11-26
[QUOTE=beew]I may be missing something but I don't think that would do what I want. If I am not mistaken setting the filter options the way you said only limits the search to installed software, but it wouldn't display all the display softwares like Synaptic does.[/QUOTE]

As I mentioned in my previous reply, you can install Synaptic and run it in a KDE environment. I do agree with you that it is a useful GUI. I have not run in KDE on a Fedora install but in the past I have run it in a Debian install with a KDE desktop. It's interesting that someone with your experience didn't think to mention Fedora in the initial post, since you were posting here.

---

### Post by oldos2er on 2010-11-26
I would agree with that. Synaptic runs perfectly well in KDE.

I haven't played much with filters in kpackagekit, not sure what they're capable of.

---

### Post by beew on 2010-11-28
I figured it out. If say you want to find all programs meeting some criteria, use the filter menu to define the criteria. And then search by description and use "any" as the search key. So to find all installed program, in the filters menu, choose only installed for "installed"and no filter for the rest. Then use "any" as the key in searching by description.

---

