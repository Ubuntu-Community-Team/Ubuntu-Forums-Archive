---
title: "BASH scripting question"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by clockworkpc on 2010-10-12
I wrote a BASH script to post blogs using GoogleCL, and I noticed something strange.

Here is the script:


[COLOR="Navy"]#!/bin/bash

# Get name of blog [TITLE]
# Gedit a text file in $HOME/Documents/Blog/[TITLE]
# Upload a blog via googlecl with "google blogger post $HOME/Documents/Blog/[TITLE]"

echo "What is the name of this blog?"
echo ""
read TITLE
echo ""
echo "$TITLE"
echo ""
gedit $HOME/Documents/Blog/"$TITLE"

google blogger post $HOME/Documents/Blog/"$TITLE"[/COLOR]

First, I saved it as blog.sh in my $HOME/Documents/Scripts and it worked perfectly.

Then, I sudo copied it no /usr/local/bin/blog (removed the .sh suffix).  When I ran it then it executed, but instead of waiting for gedit to finish it immediately executed the following line (google blogger post).

Then, I re-added the .sh suffix (sudo mv /usr/local/bin/blog /usr/local/bin/blog.sh) and it runs perfectly: it creates a text file in gedit with post title as the file name and WAITS for gedit to close before posting it.

Can anyone explain to me why this is?

---

### Post by cmnorton on 2010-10-12
I believe Linux only cares that a file has execute privs, not whether or not the file has a suffix, like .sh. I suggest putting debug echo commands of what you're opening with gedit. Also look at permissions of the files. This sounds like a full path needs to be entered when you copy the file to the /usr directory.

---

### Post by clockworkpc on 2010-10-12
> **cmnorton said:**
> I believe Linux only cares that a file has execute privs, not whether or not the file has a suffix, like .sh. I suggest putting debug echo commands of what you're opening with gedit. Also look at permissions of the files. This sounds like a full path needs to be entered when you copy the file to the /usr directory.

Thanks for your reply.

I noticed that if I had an instance of gedit open, then it would jump straight to googlecl, but if no instance of gedit was open it would wait until I had closed gedit before executing googlecl.

I have added the following lines:

[COLOR="Red"][INDENT]xcowsay --monitor=0 "Warning! killall gedit"
killall gedit
clear
[/INDENT][/COLOR]

So now the script looks like this:

[COLOR="Navy"]#!/bin/bash

### Geeky Blogs for The Inquisitive Sheep ###

# Close Gedit so that you won't post an empty blog
# Get name of blog post [TITLE]
# Get labels for blog post
# Gedit a text file in $HOME/Documents/Blog/[TITLE]
# Upload a labeled blog via googlecl with "google blogger post $HOME/Documents/Blog/[TITLE]"

xcowsay "Warning! killall gedit"

killall gedit

clear

echo ""
echo "What is the name of this blog?"
echo ""
read TITLE
echo ""
echo "$TITLE"
echo ""
echo "Any labels besides geeky? (e.g. 'label1, label2,' )"
echo ""
read LABELS
echo "$LABELS"

gedit $HOME/Documents/Blog/"$TITLE"

gnome-terminal -x xcowsay --monitor=0 """Your blog post $TITLE 
is being posted via googlecl, 
and its labels are 
geeky, $LABELS"""

google blogger post --tags "geeky,"$LABELS"" $HOME/Documents/Blog/"$TITLE"[/COLOR]

My problem is solved, but I still don't understand why if there is instance of gedit open it won't wait until gedit is closed before executing the following line.

This probably holds the key to another script I've been working on, so I'd be most appreciative if someone can enlighten me on this point.

Thanks again for your help :)

---

