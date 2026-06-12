---
title: "How to EXECUTE a file in Ubuntu?????"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Nbala on 2009-11-19
Hello, I am new to Ubuntu (love it btw) and linux, finally freed from windoze.
 But years of click the .exe and bingo there the app is, have left me dumb.
 I am **very** confused as to *how to execute a program in Ubuntu!*
 

 In particular, I am trying to execute Xsane.  
 So I found the executable, and obviously click on it, and the error comes up that 'could not open document Xsane' – 'there is no installed viewer capable of displaying the document'
 Ok... That is really quite confusing to me on many levels.   
 
[LIST=1]
[*]*Why is it 	defaulted to open as a document when file manager lists it as an 	executable?*
[*]*How does one execute an 	executable in Ubuntu???*
[/LIST]
 

 I am also having trouble with managing TeX – eg: how do I access it, where is it, I understand it is scripting ( I need it for Psych Grad work ) but if I open any .tex file, it opens as a document with no available compile or run options... So then I downloaded Kile to try to see if that would enable me to access TeX in a usable way, but now Kile is on the system somewhere, but again I have no clue as how to access it or execute it...
 It is frustrating to me as I was a poweruser in windoze- from reg editing to batching to file corrolations etc. And now Im a dumbo who cant even RUN a program or install it in a way that make it show up on a program list!!!
 

 **If anyone could answer the first questions re Xsane/executing files in Ubuntu ( why are they read as documents??? whats with that? ) I would greatly appreciate this!**
 

 **If anyone could give me some help with TeX, even telling me how to install and use a WYSIWYG GUI for TeX just, that would be a blessing, but my main question is:**
 **:KShow do you execute an executable?:KS**
 

  Thank you very much to anyone who helps- I really do appreciate this, as I need to get things going for my graduate work in helping autistic children and this would require teX (and LaTeX math) for the complex research documentation mountains created in such work. ( and sorry to be corny, but the children would also appreciate it! :D )
  

  Drew Beckett

---

### Post by philinux on 2009-11-19
With scanner switched on.

Applications>graphics>xsane

---

### Post by Nbala on 2009-11-19
> **philinux said:**
> With scanner switched on.

Applications>graphics>xsane
[COLOR=Blue]Great! That solves that particular problem :) , however there are other situations (and also just to be a decent user) where I will need to know how to execute an executable that I have installed which may not show up in the menu- eg: with teX (like LaTeX) Ive installed it and I dont see it anywhere, only if I search do I find the execute file, and then I get that pseudo-document error.
[COLOR=Red]**For my betterment, could you tell me simply how to execute an executable outside of using the menu?**[/COLOR][/COLOR]
Thank you so much= Nbala/Drew

---

### Post by lisati on 2009-11-19
> **Nbala said:**
> 
[COLOR=Red]**For my betterment, could you tell me simply how to execute an executable outside of using the menu?**[/COLOR]
Thank you so much= Nbala/Drew

One option is to use the command line (Applications->Accessories->Terminal) by typing in the program name. As with Windows, the exact details can very depending on things like whether or not it's in the path and which directory the executable file is saved.

---

### Post by Earl_Maroon on 2009-11-19
Alt+F2 opens the equivalent of Windows' Run.

If you have a file that your system doesn't detect as executable:
From the command line you can make a file executable with ```
chmod +x <file>
```
Then you can run it by double clicking on it in the file manager, or run it from the command line using its full path or (when you're in the right location) ```
./<file>
```
Most applications will run from the terminal with the command being their name already though. Any that have been installed should.

My favourite way is to use Gnome-Do to launch any programs listed in the menu.

---

### Post by philinux on 2009-11-19
> **Nbala said:**
> [COLOR=Blue]Great! That solves that particular problem :) , however there are other situations (and also just to be a decent user) where I will need to know how to execute an executable that I have installed which may not show up in the menu- eg: with teX (like LaTeX) Ive installed it and I dont see it anywhere, only if I search do I find the execute file, and then I get that pseudo-document error.
[COLOR=Red]**For my betterment, could you tell me simply how to execute an executable outside of using the menu?**[/COLOR][/COLOR]
Thank you so much= Nbala/Drew


Press Alt + F2 and enter xsane for instance would run it.

For latex not sure. Most executables are in /usr/bin. If you open synaptic and go to the latex entry then click installed files you can find the name there. /usr/bin is a defined path do you only need the name of the target most times in alf f2 or terminal.

---

