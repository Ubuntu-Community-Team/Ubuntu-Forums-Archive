---
title: "What do the default Gnome ls colors mean?"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by Matt Pellegrini on 2011-07-07
I've searched for this for ages and i can't believe a list doesn't exist.

Does anyone know the meaning of the default colors in Gnome terminal.

The main few i want to know are:

apple green
Lavender
Highlighted Green
Dark Turquoise

pictures attached i hope the color names are clear from the pictures.

---

### Post by jtarin on 2011-07-07
I don't quite get your question but maybe this will help.
> Palette

    The terminal emulation can only use 16 colors at a time to draw text. The color palette specifies these 16 colors. Applications that run in the terminal use an index number to specify a color from this palette.

    Use the Built-in schemes drop-down list to choose a preset color schemes. The color palette below and the contents of the terminal window both update to show the scheme.

    Use the Colour palette to customize the 16 default colors in the custom color palette. To customize a color, click on the color to display the Palette entry dialog. Use the color wheel or the spin boxes to customize the color, then click OK

---

### Post by MG&amp;TL on 2011-07-07
I think Matt means that he wants to know what the font colour means when he prints 'ls' or whatever.
I THINK:
dark blue is a directory.
highlighter green is an executable.

That should get you started.

---

### Post by MG&amp;TL on 2011-07-07
In fact, if you type 'file' < a space> and the the file you want to find, it will give you an output most of the time.

e.g. "file rainbowfilename"

---

### Post by jtarin on 2011-07-07
In that case:
> Once you start a gnome-terminal, you can: "Settings" --> "Preferences", to set the colors of the terminal. The way that the different files are showed it is controlled, globally, by the "/etc/DIR_COLORS" file; or as a per user basis, using, or creating a ~/.dir_colors one.

This is from my file:


# COLOR needs one of these arguments: 'tty' colorizes output to ttys, but not

# pipes. 'all' adds color characters to all output. 'none' shuts colorization

# off.

COLOR none



Below that you'll find the way to specify a color for each different file type. 

---

### Post by Matt Pellegrini on 2011-07-07
MG&TL is closest to answering my question, sorry if i wasn't clear. I wasn't after changing the colors, just wanted a list of the default colors.

Basically i thought along the lines of what MG&TL is saying but then i found that a jpg file saved under ~/Pictures/file.jpg is listed pink when i do ls but ~/Music/ArtistAlbum/coverart.jpg is green, so how can it just be to do with file type.

I'm fairly sure they're not links as ls -l doesn't bring up the path.

Thanks for continued help guys

---

### Post by MG&amp;TL on 2011-07-07
I don't know, possibly pink means that it's directly under a pre-installed directory.

Try copying the file in /pictures to the /documents location, you can do this graphically or via terminal:

"cp <put pictures file path here> <put documents file path here>"

See what colour it goes then.

Have you edited one picture but not the other?

---

### Post by Matt Pellegrini on 2011-07-07
Actually i think the difference was down to the permissions for each file. Thus the apple green i was referring to could mean an executable file?

And pink means read only?


Can anyone confirm this?

---

### Post by MG&amp;TL on 2011-07-07
Well, there's an easy way to check- try:

cd to containing directory
"./""<apple green thing>"

./ means execute a program, sorry to be patronising if you knew that.

for the read-only, see whether you can open and edit the file, then see if you can save it without using sudo or whatever. If so, then it's not read-only (by definition)

---

### Post by compmodder26 on 2011-07-07
Files that have a green background are writable by everyone.  Files with a green font are executable.  Blue text indicates a folder.  Image types are generally purple. Gzipped files are usually red.  Light blue text indicates a symlink. Blue background means hard link.

---

### Post by Matt Pellegrini on 2011-07-07
./ doesn't mean executable, it just means current directory, you can use it to launch executable files in the current directory.

Anyway i think we should leave the thread here unless someone knows for sure.

All i'll say is that with the executable bit set the file displayed green, without jpg were pink and audio files dark turquoise. I think my permission bits are still different to the default so people reading this should check that. Sorry this post wasn't more help.

Here's still hoping someone can post a link to a definitive list.

---

### Post by sisco311 on 2011-07-07
```

dircolors -p
```
or:
```

while read -r line
do
    echo -e "$line"
done< <(dircolors -p | sed -r -e 's/(([0-9][0-9];)+)([0-9][0-9])/\\e[\1\3m- color: \1\3 \\e[00m/')

```

---

### Post by Matt Pellegrini on 2011-07-08
@compmodder26  Thanks, this is exactly what i was after and seems to agree with what i have found, thanks.

---

### Post by Matt Pellegrini on 2011-07-08
if anyone else wants to add to compmodder26's list that would be great if you look back at my original pictures, what does the .flac file color mean? If we get a few more colours solved i'll mark the thread as solved,

Thanks

Matt

---

### Post by Matt Pellegrini on 2011-07-08
> **sisco311 said:**
> ```

dircolors -p
```or:
```

while read -r line
do
    echo -e "$line"
done< <(dircolors -p | sed -r -e 's/(([0-9][0-9];)+)([0-9][0-9])/\\e[\1\3m- color: \1\3 \\e[00m/')

```


Thanks, i've seen this before but never understood it until now, how can i edit this file, say to include .wma in the audio file section?

I know how to edit it, just where is it stored?

Thanks

---

### Post by Matt Pellegrini on 2011-07-08
Ill add this table i finally found and mark the thread as solved, hopefully this is enough for anyone reading this now solved thread. If the color your looking for has not been mentioned here then i can only add the knowledge that colors are based on file type and permissions, ls -l to find permissions to see if there is anything special about the permissions, like can everyone write to it (green), if not then it's probably just the file type.

Color File type     blue directories   red compressed archives   white text files   pink images   cyan links   yellow devices   green executables   flashing red broken links

---

