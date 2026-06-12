---
title: "please help"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by drunkfest on 2008-12-11
ok so when i got download wine in synaptic package manager.. i search for wine and nothing shows up......

why?

can someone pleace help me download it?

---

### Post by chavy85 on 2008-12-11
in the package manager just install playonlinux.
or sudo apt-get install playonlinux

---

### Post by adult swim on 2008-12-11
go to system>administration>software sources and make sure that the four boxes are checked.  then search synaptic again.

---

### Post by nakama85 on 2008-12-11
> **drunkfest said:**
> ok so when i got download wine in synaptic package manager.. i search for wine and nothing shows up......

why?

can someone pleace help me download it?



I find the esiest way to download apps is in terminal
```
sudo apt-get update
sudo apt-get install wine
```

it should be under applications--->Wine
but if not try and restart your computer and see if it shows up.

if still does not, let me know.
[I]
note: Your thread title should be more descriptive fo a better chance of getting help more quickly[/I]

---

### Post by Shwefty on 2008-12-11
You could use Applications -> Add/Remove Programs, follow Adult Swim's advice about the checkboxes, but also make sure that under "Show:" the drop down menu reads "All available programs".  Then, type Wine into the search bar, check the "Wine Microsoft Windows Compatibility Layer" box and hit "Apply Changes".

---

### Post by growlf on 2008-12-11
mm..  also, you could get it in a happy little deb pckage hot off the press at WineHQ:

[http://www.winehq.org/download/](http://www.winehq.org/download/) 

...note the Ubuntu link at the top, courtesy of Scott Richie.  Just click and install.

I tend to go this route because it is frequently somewhat newer than the repo version and is stable as well.

---

### Post by drunkfest on 2008-12-11
alright so i tried all of those but it still doesnt show up

are there any other programs that work like wine?

---

### Post by nakama85 on 2008-12-11
> **drunkfest said:**
> alright so i tried all of those but it still doesnt show up

are there any other programs that work like wine?

does wine run when you type "wine" in terminal?


you could try crossover

---

### Post by growlf on 2008-12-11
Sure there are others.. well.. kinda.  They are all based on Wine though for the most part.  Cedega comes to mind.  Other alternatives such as Sun's VBox or QMware as a virtual computer solution too.  

But seriously.. WineHQ has it in a quick and easy click-to-install deb on te page I mentioned above.  It is about the simplest way for installing it.

---

### Post by drunkfest on 2008-12-11
nope nothing is working:/

ill try it 

im trying to just download wine from the wedsite
hopfully that works

---

### Post by drunkfest on 2008-12-11
ok so i donwloaded it sucefully from the site

but now i cant find it
or did it ever really download

cuz i got the it to say it was then it just closed

---

### Post by growlf on 2008-12-11
..should show up near or at the bottom of the Applications menu...  there will be a demo app installed there as well I think, notepad.  

Just a thought, it DID ask to run it with gdebi when you clicked it right?  ..and you then told it to go ahead..  right?

---

