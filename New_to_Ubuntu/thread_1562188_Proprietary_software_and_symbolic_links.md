---
title: "Proprietary software and symbolic links"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by srnissen on 2010-08-27
I have recently installed the student version of MATLAB on my system. Unfortunately, it would appear that I did not set up symbolic links.

If I simply delete the folder I installed MATLAB to and start over, will this leave various bits and pieces of the software around my computer, as a similar act would do in Windows?

Follow-up question:
How do I set up a symbolic link? Having installed MATLAB without symbolic links, I cannot simply type "matlab" in the terminal. The manual indicates that this would otherwise have linked to /matlabroot/bin/matlab which, yes, does start up MATLAB - is there some way of creating a symbolic link on my own, so I won't have to do a re-install to get it?

Follow-up follow-up question:
IF it happens that there is a way to set up a symbolic link on my own, how do I set about removing it when I, eventually, want to remove MATLAB? (e.g. in two years when my license runs out, or when I start using octave instead, or...)

Tripple-follow-up-question:
The reason I'm using MATLAB is because I couldn't find a way of changing octave so the command "edit test.m" started test.m in an editor that isn't emacs. It's emacs by default, apparently, but I'd rather use something else. Is this possible? If so, I'd like to know how?

---

### Post by dv3500ea on 2010-08-27
I'm not sure how MATLAB sets itself up but I think that probably just deleting the folder will work.

You can set up a symbolic link using this command:

```
sudo ln -s /matlabroot/bin/matlab /usr/bin/matlab
```

You can remove the symbolic link with this command:

```
sudo rm /usr/bin/matlab
```

You can edit .m files using any text editor (Gedit has syntax highlighting for .m files by default - although it may detect them as objective c files so you have to change the file type to 'Octave': View -> Highlight Mode -> Scientific -> Octave).

You can change the editor used by the [edit]("http://octave.sourceforge.net/octave/function/edit.html") function by adding these to lines to the file ~/.bashrc
```

EDITOR=gedit
export EDITOR

```
replacing gedit with your preferred text editor.

---

### Post by srnissen on 2010-08-27
> **dv3500ea said:**
> Snip answers

Thank you, that took care of all my questions. (Except the first one, but I found the answer in the manual - you can, indeed, just delete the matlab folder.

EDIT: Now I'm just curious how to change the thread tag from [Ubuntu] to [Solved]
EDIT2: Never mind, found it.

---

