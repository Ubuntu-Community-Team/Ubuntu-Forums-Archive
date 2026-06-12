---
title: "Obtaining write access to a file, which is not in the home directory"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by gemm on 2009-07-02
Hi,

I am using Ubuntu 8.10. I want to modify a file, which is not in my home directory, but I seem not to have write access to it, and I do not know how to modify it.

I have installed a package, texlive-humanities, via the Synaptic Package Manager. In this package there is a package xyling, which is the one I am interested in. The package manager installs everything automatically, but via "Search .." I managed to find the xyling folder with the correspodning files inside, here:

/usr/share/texmf-texlive/tex/latex/xyling

In this folder there is a file, xyling.sty, which I want to modify. I can open the file, and change what I want, however, I cannot save my changes, because the Ubuntu says: "The document could not be saved, as it was not possible to write to file:///usr/share/texmf-texlive/tex/latex/xyling/xyling.sty. Check that you have write access to this file or that enough disk space  is available."

I seem not to have write access. The only change I want to do in the file is modify the line:
\RequirePackage[color,all,dvips]{xy}
to
\RequirePackage[color,all]{xy} 

If I open a console, I have access only to my user profile: my prompt is at gemm@computer:~$
and I cannot access the xyling.sty file which is in /usr/share ..... directory. I know that if I want to invoke a program being as root, I have to type "sudo" and then the program name. However, here I cannot access the xyling.sty from anywhere: it is not in my home directory. Could you tell me how can I modify the file (obtain write access to it)?
Thank you.

---

### Post by PureLoneWolf on 2009-07-02
Hi

Try:

```
gksu gedit /usr/share/texmf-texlive/tex/latex/xyling/xyling.sty
```

You will be prompted for your password, but you should then have access to write to the file.

---

### Post by austinpsycho on 2009-07-02
lets back up a second here; in your terminal, basic navigation:
*cd /*  will get you to your root directory; [I]
ls  [/I]will get you a listing of directories and files
you can type Tab after partially typing in the next foldername like *cd /e*[tab] will make it say [I]cd /etc
[/I]you can navagate directly to the folder with: *cd */usr/share/texmf-texlive/tex/latex/
I would just *sudo chmod xyling w* (i think thats the context) or you can *sudo nautilus  *and change the permissions by navigating in the window that pops up and right clicking on the file and going to properties, add write to your permissions an violla

---

### Post by gemm on 2009-07-02
Thanks a lot, guys!!! 
I tried all the things you wrote, and it all worked fine.
Very basic things, but I didn't know them. Feel a better now :)
Thanks!

---

### Post by oldos2er on 2009-07-02
If you install the package nautilus-gksu, you can simply right-click on a file and choose 'Open as administrator'. It's a handy plugin.

---

