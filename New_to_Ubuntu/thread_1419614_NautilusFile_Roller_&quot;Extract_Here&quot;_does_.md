---
title: "Nautilus/File Roller: &quot;Extract Here&quot; does NOT actually extract to &quot;Here&quot;"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by auh2o on 2010-03-02
When extracting an archive (in this case, zip files) that does not contain a folder structure, but simply one or several files, by right-clicking on the archive in Nautilus and choosing "Extract Here", the result is that the files are extracted not to "Here" - i.e. the folder containing the archive - but to a sub-folder with the name of the archive. How do I correct this function into doing what it actually says? I have dozens of zip-files that I want to extract in this manner into the *same* folder, and not get a separate folder for each archive.

I suppose I could add a menu item with nautilus-actions that will do what I want (and if anyone would like to tell me how, I'd be obliged), but that would still leave the faulty "Extract Here" in place. If it could be removed somehow, it might be better to add several nautilus actions, much like the WinRAR and WinZip Explorer shell menus, so that I could have a choice of extracting to "Here" or to "Here/<archive name>/*.*"

---

### Post by Kazade on 2010-03-02
I believe the function is working as intended. It's designed to extract to a subfolder so that you don't get files dumped everywhere when the creator of the archive forgot to compress the files inside a folder... something that WinZip used to hit me with a lot! :)

The easiest thing to do is to perhaps just double click the archive (e.g. open it in archive manager), select the files, then drag and drop them in the folder you want.

---

### Post by r-senior on 2010-03-02
I can only speculate but I suspect the behaviour of "Extract to Here" is intended to avoid accidental spilling of an archive into a directory from which it could be difficult to clean. Not that that helps you of course. ;)

Would you consider using a single command in a terminal? 

$ find . -maxdepth 1 -name '*.zip' -exec unzip {} \;

This finds all zip files ("*.zip") in the current directory (".") but not subdirectories ("maxdepth=1") and executes a command ("unzip") with each zip file name passed as a parameter ("{}"). The "\;" signifies the end of the parameter list.

---

### Post by auh2o on 2010-03-04
Alright, so the two replies I have thus far gotten suggest:

1) Open the Archive Manager and extract the files from within it. (And how this would be deemed easier than a simple right-click>extract I'll never know)

2) Use the bloody* terminal*. 'Nuff said.

Not to rip on you guys - I do appreciate your replies, after all - but you realize of course that these two ways of extracting totally defeats the purpose of having an easily accessible Nautilus menu option in the first place, right?

Yes, I have no doubt the "Extract Here" command is working as intended. The only problem is, whichever dev is responsible for it intended it **wrongly**. It simply does not do what it says. It extracts to Here/Subfolder, not to Here. In the WinZip and WinRAR context menus I am provided with *both* alternatives. That's what I want in Nautilus too. And if I can't alter or delete the standard command, I will at least add another one to do what I want - and maybe name it Extract to *HERE* to be able to tell them apart!

*This* is where I will need help with a command line. I'll create a new action matching all forms of archives that the Archive Manager can handle. But what do I then put in the command line field in Nautilus Actions?

Of course, I don't have to call up the Archive Manager; maybe it's better to use 7zip. And if so I can probably piece together a command string from the 7zip help, feeble prior Windows user though I am.

In the meantime, r-senior, I tried your terminal command to extract all those zip-archives I currently needed in the same folder, and it worked like a charm. Thanks!

---

### Post by auh2o on 2010-03-05
Alright, since inexplicably nobody else seems to think it a problem that a command doesn't do what it actually says, I've been tinkering with Nautilus Actions to create a real Extract Here command. So far to no avail. Is it possible to use 7zip this way? A simple *7z e -y *command line does nothing. Does anyone know how the standard context menu item is written? Do I have to set different actions for different acrhives, i.e. use unzip, unrar etc.? Does file-roller work with a command line?

---

### Post by r-senior on 2010-03-05
With Nautilus Actions I think I get what you want by entering these values under "Action" on the "Action" tab:

Path: /usr/bin/unzip
Parameters: -o %M

On the "Conditions" tab I set filenames to *.zip. The others depend how you want to play it. I set selection to "only files" and didn't test the multiple selection but it should work.

I'd urge you to read the manual page for unzip to understand the options, especially -o which overwrites without prompting.  Click on your blue help icon and type "man unzip" in the search box, or type "man unzip" in a terminal (go on, you know you want to open that terminal and feel its power ;)).

---

### Post by Paddy Landau on 2010-03-05
> **auh2o said:**
> ... since inexplicably nobody else seems to think it a problem...
I beg to differ. I find it a **blessing** that it does this; on several occasions it has prevented me from accidentally filling a folder with many files. Bearing in mind that Ubuntu is designed (in theory, at least, if not entirely in practice) to be easily used by newbies, I agree with the current structure.

If you were to add a new option to Nautilus, may I suggest changed wording? Thus, the existing "Extract Here" would be renamed to "Extract to folder <name>", and your new line would be called something like "Extract to current folder". This would eliminate confusion and cater for everyone, including newbies, people with little technical know-how (apparently Ubuntu's target market), and more sophisticated users (like you).

Have you considered filing this as a feature request for Nautilus?

---

### Post by auh2o on 2010-03-05
> **r-senior said:**
> With Nautilus Actions I think I get what you want by entering these values under "Action" on the "Action" tab:

Path: /usr/bin/unzip
Parameters: -o %M

On the "Conditions" tab I set filenames to *.zip. The others depend how you want to play it. I set selection to "only files" and didn't test the multiple selection but it should work.

I'd urge you to read the manual page for unzip to understand the options, especially -o which overwrites without prompting.  Click on your blue help icon and type "man unzip" in the search box, or type "man unzip" in a terminal (go on, you know you want to open that terminal and feel its power ;)).

Yes, that works, but that would mean creating a separate action for every type of compressed archive that I am in one or another way able to handle. It's doable of course, but it would be much neater to create one action that included all archive types, like the original entry. (How is that written, by the way?). This is why I thought using 7zip would be good, but simply entering the 7z e (or x) -y line doesn't do anything. In the terminal window this would work fine, but I must be missing something to make it work as a Nautilus action.

> **Paddy Landau]I beg to differ. I find it a **blessing** that it does this said:**
> 

It is perfectly alright for you to differ. And that alone is reason enough that there should be *two* alternatives. One man's blessing is another man's curse. Virtually every archive manager that has the option to add a context menu to Windows Explorer offers BOTH alternatives, and "Extract Here" always means exactly that. That's what I want in Nautilus too. I will make use of both alternatives at different times, and I don't want to be constrained to one of them.

[QUOTE=Paddy Landau]If you were to add a new option to Nautilus, may I suggest changed  wording? Thus, the existing "Extract Here" would be renamed to "Extract  to folder <name>", and your new line would be called something  like "Extract to current folder". This would eliminate confusion and  cater for everyone, including newbies, people with little technical  know-how (apparently Ubuntu's target market), and more sophisticated  users (like you).

Changing the existing entry is something that can not be done with Nautilus Actions. I can only add new entries. It don't doubt that it is possible to alter or remove it, but that surpasses my knowledge.

Sophisticated user... I don't know. Everything is relative! I'm hoping a *more* sophisticated user will drop by and set the record straight on how to do this.

---

### Post by r-senior on 2010-03-05
You could use file-roller as you suggested?

The manual page for file-roller covers the options:

$ man file-roller

Press "q" to quit. The -e option to file-roller specifies the extract folder. Nautilus provides the %d substitution as the directory where you triggered the action in Nautilus.

Then of course, you'd need a list of matching filename patterns associated with the Nautilus Action. Hovering on the requisite input field suggests you can specify a list of patterns separated by ";".

Your other archive program may not be working from Nautilus because you haven't specified the full path to it. You can use the "which" command to find it.

$ which <command>

---

### Post by Jordanwb on 2010-03-05
> **r-senior said:**
> I can only speculate but I suspect the behaviour of "Extract to Here" is intended to avoid accidental spilling of an archive into a directory from which it could be difficult to clean.

That is correct. Wikipedia:

> Tarbomb: A tarbomb is derogatory hacker slang used to refer to a tarball that does not follow the usual conventions, i.e. it contains many files that **extract into the working directory**.

---

### Post by auh2o on 2010-03-05
r-senior, thanks for your help. I'll get to work.

---

### Post by jcottier on 2010-07-23
I have the opposite problem on fresh intall of ubuntu 10.04. When I right click and choose "Extract Here" it does just that (not in a folder) and if the file exists it renames appended with "(copy 1)" etc. I guess they changed it. Previously KDE3's Konqueror (now a distant memory sadly) used to have several extract/compress right click options, including one for extracting to a folder of the same name as the archive. I used this a lot so I really miss it. I wish there was an easy way to configure Nautilus or add an action to do this. Probably easy with a script if you know how.

---

### Post by beew on 2010-07-23
Download and install Peazip. File roller is a piece of crap.

[http://peazip.sourceforge.net/]("http://peazip.sourceforge.net/")

---

