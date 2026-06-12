---
title: "GEdit: Search and Replace in selection only??"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by theoryl on 2010-04-12
I like GEdit, but it doesn't allow me to search and replace within selected text only. Does anyone know how to get this feature in GEdit? Thank you!

---

### Post by BBUCommander on 2010-05-07
I would very much like to know this as well.  I love using Gedit for coding, but the lack of a replace in selection feature keeps me from using it as my primary editor.

---

### Post by vamped on 2010-05-21
That is exactly my problem too today.

It seems there should be a plain_text editor with some bells and whistles too - but one that loads quickly like gedit. I have not experimented yet with the other editors available, and was hoping someone could save me a lot of time.


p.s. OO-Write loads too slowly, but that is nothing compared to the additional setup that has to be done after the file is loaded: Write tries to format it to the current printer/page size, etc. and I have not figured out how to put Write into a text-mode. (No just changing to a mono-space font is not the same)

---

### Post by ljrmorgan on 2010-06-13
Yeh, I just came across this too - I really don't understand why there isn't an option in the "replace" dialog that lets you replace text from the selected text only. I can't imagine it would be hard to add, seems like an odd thing to miss out/overlook. GEdit is still great though :-)

---

### Post by lost_in_transylvania on 2010-06-13
This has been bugging me too... 

So here is an admittedly hackish (gedit) snippet to implement this functionality:

```
$<
lines = $GEDIT_SELECTED_TEXT.split("\n");
nlines = len(lines);
output = "";
a = "";
b = "";
cnt = 0;
for line in lines:
    cnt += 1;
    if cnt == 1:
        a = line;
    elif cnt == 2:
        b = line;
    elif cnt != nlines:
        output += (line.replace(a,b) + "\n");
    else:
        output += (line.replace(a,b));
return output;
>
```This works as follows - 

On the 2 lines prior to the text to be selected, type the target string and then the replacement (these must be on separate lines). Then select the text (including the target and replacement you just typed). Use your preferred keyboard shortcut to trigger it.

There is no ability -- yet -- to restrict the search/replace operation to whole words. However, it shouldn't be to difficult to accomplish this with the re built-in and some tweaking of the above code...

If anyone wants to make that happen, I won't try to stop you! Or, I just might do it myself when I find the time....

Now, of course, this should really be implemented as a dedicated plugin, not via snippets. And, again, if anyone wants to make that happen, I won't try to stop you!

---

### Post by Calmarius on 2010-12-22
[off]

Ubuntu and open source sofware is nice, but who makes open source software usually make software for himself without thinking about others need. 

That's why gedit doesn't have the ability to search and replace text in selection... Also, archive-manager overwrites files without asking, pff...

Both problem could be solved by addig several lines of code I think and everybody would be happy.

[/off]

Unable to replace and search text in selection is very annoying. Mainly if you don't know about it, select some text and replace something and bang... And you realize the damage you did days after, pfff

---

### Post by john77eipe on 2010-12-22
> Ubuntu and open source sofware is nice, but who makes open source software usually make software for himself without thinking about others need.

I think you are wrong there... open source is were people contribute according to the requirements they perceive during the development. If later a certain functionality is highly voted for, then it will be included in the next release. 

Or as it is open source, anyone can contribute and get in touch with the developers.

---

### Post by AngusH on 2010-12-22
This is far from a perfect solution, but as a quick way to get the functionality you want. Put the cursor on the first line of the selection of text, use the find and replace tool, close the box once you reach the end of the area you want to do. Not a good solution, but a working one.
Angus

---

### Post by mcduck on 2010-12-22
> **john77eipe said:**
> I think you are wrong there... open source is were people contribute according to the requirements they perceive during the development. If later a certain functionality is highly voted for, then it will be included in the next release. 

Or as it is open source, anyone can contribute and get in touch with the developers.

+1 to this.

Besides, the majority of open-source contributors in larger projects (like Gnome) actually are paid by companies, and do it for living. Linux and open-source software being hacked together by hobbyists is just a misconception.

Not to forget that Gedit has a great plugin framework as well. So anybody interested in adding such search functionality is able to do that even on his own, without having to mess with the main application itself or to work with Gedit's developers at all. :)

That being said, you'll probably want to go through the selection of available plugins, and check if one of them would provide the functionality you are looking for: [http://live.gnome.org/Gedit/Plugins]("http://live.gnome.org/Gedit/Plugins")

---

### Post by wim.glenn on 2011-06-06
holy revived thread , batman !!  

[http://code.google.com/p/advanced-find/](http://code.google.com/p/advanced-find/)

---

### Post by Guido Tabbernuk on 2012-01-21
> **AngusH said:**
> This is far from a perfect solution, but as a quick way to get the functionality you want. Put the cursor on the first line of the selection of text, use the find and replace tool, close the box once you reach the end of the area you want to do. Not a good solution, but a working one.
Angus
Thanks, previously I was copying my text to new tab, searching/replacing the strings there, and then closing the tab and copying the snippet back again. But, yes, the solution is kind of manual thing, causing extra keystrokes and waisting finger power, especially with larger selections.

Has anybody repeated it as a bug in gedit? Oh, it's [https://bugzilla.gnome.org/show_bug.cgi?id=150010](https://bugzilla.gnome.org/show_bug.cgi?id=150010)

---

