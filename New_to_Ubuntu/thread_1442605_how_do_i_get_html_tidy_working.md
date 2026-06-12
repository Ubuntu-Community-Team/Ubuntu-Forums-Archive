---
title: "how do i get html tidy working"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by mike101 on 2010-03-30
Hello

I'm new to Linux. 

I've installed html tidy from the synaptic package manager but can't work out how to get it running.

I've found it in usr/bin/tidy as an executable file. I've tried right clicking and opening it with various text editors which doesnt work ( most say can't load binary file). 

I'd be grateful for any advice..

---

### Post by diesch on 2010-03-30
It's a command line program. Open a terminal and type
```
 tidy -o output.html input.html
```
to read *input.html* and write to* output.html*. See the [man page](http://manpages.ubuntu.com/manpages/karmic/en/man1/tidy.1.html) for more information on how to use it.

---

### Post by mike101 on 2010-03-30
> **diesch said:**
> It's a command line program. Open a terminal and type
```
 tidy -o output.html input.html
```to read *input.html* and write to* output.html*. See the [man page]("http://manpages.ubuntu.com/manpages/karmic/en/man1/tidy.1.html") for more information on how to use it.

When I try that  I get this error code

Error: Can't open "input.html"

---

### Post by diesch on 2010-03-30
*input.html* is the HTML file you want to tidy up. Replace it with any other file name if you want.

---

### Post by mike101 on 2010-03-31
> **diesch said:**
> *input.html* is the HTML file you want to tidy up. Replace it with any other file name if you want.

Ahh ok thanks

But now when I type 
tidy -o output.html /home/desktop/about-me.html (for the html files named about-me

I get this error

Error: Can't open "/home/desktop/about-me.html"

I can open the file in a text editor and preview it in Mozilla

I've tried writing the full path for the html file (home/documents/ etc) but this doesnt work either..

Any ideas most welcome

---

### Post by VernonA on 2010-03-31
Are you sure the file you want to tidy is really called "/home/desktop/about-me.html"? I bet you have mis-typed somewhere. Go to the "/home/desktop" and type ls to see what files it contains. Is about-me.html listed? In other words try:
```
cd /home/desktop
ls *.html

```Perhaps the file is on your home directory instead? Try:
```
cd ~
ls *.html
```
Does this find it?

---

### Post by JKyleOKC on 2010-03-31
> **mike101 said:**
> when I type 
tidy -o output.html /home/desktop/about-me.html (for the html files named about-me

I get this error

Error: Can't open "/home/desktop/about-me.html"

I can open the file in a text editor and preview it in MozillaI suspect you have at least two things wrong here, both fairly simple.

The first is that the "/home" directory cannot be opened with "write" permission except by the super user. This may be causing tidy to error out.

More likely the "desktop" part of the path should be "Desktop" since Linux (unlike Windows) is case sensitive.

Finally, is "desktop" an actual user ID on your system, or is it supposed to be the desktop for your user ID? If the latter, it's not located in "home" but is part of "/home/mike" if "mike" is your user ID.

Try ```
tidy -o output.html $HOME/Desktop/about-me.html
``` instead, making sure to have HOME in all upper case and Desktop capitalized. This will automagically expand to your home directory without running into the first possibility I mentioned, and if "about-me.html" really is in your Desktop directory, should work...

---

### Post by teward on 2010-03-31
yo u COULD just navigate through command line to where the file is then run tidy, should operate on the same principles as any other command that if you don't specify an actual path, it will search in the currently accessed directory.

---

