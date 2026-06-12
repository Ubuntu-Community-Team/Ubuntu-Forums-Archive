---
title: "What is meaning of command parameters starting with %"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Ralph L on 2009-05-17
I notice that under right click Main Menu>Edit Menus>Properties many of the commands have a parameter of %u or %U.  Also, some web sites dealing with Amarok iPod eject recommend inserting %d or %m in the post disconnect command as in "echo "a" | sudo -S eject -m %d".  I don't understand the meaning of this parameter and why it is used.  Can anybody help me?

Incidentally when I added to Amarok "echo "a" | sudo -S eject -m %d" as a post disconnect command, it ejected my cd rather than my iPod.  Any ideas of how I change the command to cause it to eject my iPod?

Thanks

Ralph

---

### Post by s.fox on 2009-05-17
Hi,

You could just right-click the IPOD on the desktop and unmount it.  :)  

-Ash R

---

### Post by diablo75 on 2009-05-17
I couldn't find anything about that %d parameter in the eject manual, but you might glance at it to see if you can find a way to change the command to do what you want.  To see the manual, open a terminal and type "man eject" without the quotes.  It'll describe all the options and command syntax you need to get it to work.

---

### Post by Ralph L on 2009-05-21
The % character obviously means some source of substitution of the command parameter, but I have never seen this documented and don't know where to look.  And more importantly I don't know where the substituting parameters comes from.

Here is another example that I use in Amarok:  faac -b 128 --title %{title} --comment %{comment} --artist %{artist} --album %{albumtitle} --year %{year} --track %{number} --genre %{genre} -w -o %o %f

Any more suggestions?

Thanks

Ralph

---

### Post by mcduck on 2009-05-21
Most common use for those variables is to allow drag&dropping things to the launcher to open it in the program.

**%f**
A single file name, even if multiple files are selected. The system reading the desktop entry should recognize that the program in question cannot handle multiple file arguments, and it should should probably spawn and execute multiple copies of a program for each selected file if the program is not able to handle additional file arguments. If files are not on the local file system (i.e. are on HTTP or FTP locations), the files will be copied to the local file system and %f will be expanded to point at the temporary file. Used for programs that do not understand the URL syntax.

**%F**
A list of files. Use for apps that can open several local files at once.

**%u**
A single URL.

**%U**
A list of URLs.

**%d**
Directory containing the file that would be passed in a %f field.

**%D**
List of directories containing the files that would be passed in to a %F field.

**%n**
A single filename (without path).
[B]
%N[/B]
A list of filenames (without paths).

**%i**
The Icon field of the desktop entry expanded as two parameters, first --icon and then the contents of the Icon field. Should not expand as any parameters if the Icon field is empty or missing.

**%c**
The translated Name field associated with the desktop entry.

**%k**
The location of the desktop file as either a URI (if for example gotten from the vfolder system) or a local filename or empty if no location is known.

**%v**
The name of the Device entry in the desktop file.

edit: Check this link for more information: [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-0.9.4.html#exec-variables]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-0.9.4.html#exec-variables")

---

