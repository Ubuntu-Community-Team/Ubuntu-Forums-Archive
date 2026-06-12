---
title: "dissapearing windows"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by dzon65 on 2009-10-31
When I have a document open,minimalize it and open a new one,the previous one closes.How can I set it to keep the previous one open in ubuntu 9.10?

---

### Post by diablo75 on 2009-10-31
I don't know if you're talking about Open Office, or gedit, or something else, but it likely isn't closing the document.  It's probably opening the new one in a new tab, like Firefox does when you open a new tab.  There might be an exception to his rule if you're using evince to view PDF files, but I really don't know.  But again, I really really doubt the file you've open is closed so as to allow another one to open. Look hard.

---

### Post by dzon65 on 2009-10-31
No,it's really gone.In this case I was checking into the gtkrc of a theme I'm using.I wanted to edit it with some stuff I have stocked in my documents.The moment I click the file I'm looking for,the gtkrc file closed.No tabs,no nothing.I had to reopen it,but the moment I open it,the document file closes.Again,no tabs nothing.

---

### Post by The Cog on 2009-10-31
What editor is this?
Try launching the editor from the command line to see if it outputs a crash message as it closes.

---

### Post by dzon65 on 2009-11-01
Gedit.It's gedit that keeps doing this.Don't have this problem with other windows exept the gedit ones.I posted something about gedit being veeery slow.(jerky,as well when browsing in a gedit file as copying text).So,how can I check this?

---

### Post by emigrant on 2009-11-01
while one gedit is open.
go to termeinal and 

```

gedit destination filename &

```

---

### Post by dzon65 on 2009-11-01
Ok,uninstalled and reinstalled gedit.Put in that command.I'm having tabs in the gedit window now but browsing a a bit larger file is still jerky and I can't open two files next to eachother.Can't have two gedit files in seperate windows at the same time.It's a bit difficult when wanting to compare files using tabs as you can understand.

---

### Post by The Cog on 2009-11-01
That's really odd. If you press F9 to get the side pane, do you see both open files listed there? I am wondering if it's just that the tabs bar has gone missing. 

For side-by-side file comparison, try **meld**.

---

### Post by dzon65 on 2009-11-01
Just a sec,just reinstalled 9.10.Have to make some files.

---

### Post by dzon65 on 2009-11-01
Pressing F9 does show the files in the side panel,as do the tabs.It's just that I can't open them side by side.I'll check the suggestion you made.

---

### Post by dzon65 on 2009-11-01
Yep,can put them alongside.Thanks for the tip.Up to the next problem,perhaps you have any ideas on this.I posted it as bluetooth??? ubuntuforums.org/showthread.php?t=1309069

---

