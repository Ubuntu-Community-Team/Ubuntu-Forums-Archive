---
title: "Random terminal colors"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by =CrAzYG33K= on 2010-06-20
I want to have random colors on my terminal. Let's say I have a list of 10 pre-defined foreground and background color combinations stored somewhere. Everytime I invoke terminal, I want some script to to pick up a random color from the list and invoke the terminal using that. Is there an app that accomplishes this ? Or a link to a BASH script that does it?

---

### Post by VastOne on 2010-06-20
> **=CrAzYG33K= said:**
> I want to have random colors on my terminal. Let's say I have a list of 10 pre-defined foreground and background color combinations stored somewhere. Everytime I invoke terminal, I want some script to to pick up a random color from the list and invoke the terminal using that. Is there an app that accomplishes this ? Or a link to a BASH script that does it?

From within terminal, you can have as many profiles as you want and then invoke which one you want when you start terminal.  Not as clean as a script, but effective.

---

### Post by =CrAzYG33K= on 2010-06-20
> **VastOne said:**
> From within terminal, you can have as many profiles as you want and then invoke which one you want when you start terminal.  Not as clean as a script, but effective.

I know that, but I wanted an elegant script which would invoke random defined colors from an already defined source everytime I invoked terminal.

---

### Post by VastOne on 2010-06-20
> **=CrAzYG33K= said:**
> I know that, but I wanted an elegant script which would invoke random defined colors from an already defined source everytime I invoked terminal.

[[COLOR="Red"]_This_[/COLOR]]("http://code.activestate.com/recipes/576503-linux-terminal-color-setter/")  should give you the know how to create your scripts. 

Found by googling Linux + Terminal + Color

---

### Post by =CrAzYG33K= on 2010-07-01
@VastOne

That thing just drives me crazy. I wanted a simple tweak to probably change my terminal color every time I opened up Terminal.. Python is probably the last thing that I'd want to try on.

Something simpler, uhm, like modifying by .bashrc script?

---

### Post by ibuclaw on 2010-07-01
OK, no testing has been done here, just going off on a tangent presuming this will work.

OK, I assume you use Gnome Terminal. Gnome Terminal colours are no longer customisable via a startup switch (and haven't been for some time).

You can, however, write a wrapper script that:
[LIST=1]
[*]Has a predefined list of colours to mix
[*]Chooses a random one
[*]Sets the random colours via gconftool-2, and starts the real gnome-terminal.
[/LIST]

```

#!/bin/sh

# Predefined colour sets.
BG_COLOURS=(
    FFFFFFFFDDDD  # Cream Yellow
    FFFFFFFFFFFF  # White
    000000000000  # Black
    000000000000  # Black
    000000000000  # Black
)

FG_COLOURS=(
    000000000000  # Black
    000000000000  # Black
    AAAAAAAAAAAA  # Grey
    0000FFFF0000  # Green
    FFFFFFFFFFFF  # White
)

# Number of elems in the array.
NUM=${#FG_COLOURS[@]}

# Pick a random number
ELEM=$(($RANDOM % $NUM))

# Set colours
gconftool-2 --type string --set /apps/gnome-terminal/profiles/Default/background_color "#${BG_COLOURS[$ELEM]}"
gconftool-2 --type string --set /apps/gnome-terminal/profiles/Default/foreground_color "#${FG_COLOURS[$ELEM]}"

# Start gnome-terminal
exec /usr/bin/gnome-terminal.distrib "$@"

```


And to install:
```

sudo dpkg-divert --local --rename --add /usr/bin/gnome-terminal
sudo install **script-name.sh** /usr/bin/gnome-terminal

```
And to uninstall:
```

sudo unlink /usr/bin/gnome-terminal
sudo dpkg-divert --local --rename --remove /usr/bin/gnome-terminal
```

Some playing will be needed, yes. But hopefully a step in the right direction. :)

---

### Post by =CrAzYG33K= on 2010-07-01
Many thanks for the script, but now I guess I've screwed up my terminal. It wouldn't open up at all anymore..

How do I uninstall it now and come back to the previous state? :o

**EDIT:**

I managed to do the 'uninstall' part coz' luckily I had another Terminal window open somewhere else.
So why did Terminal refuse to open ??

---

### Post by lkjoel on 2010-07-01
You could literally create a cheap terminal...
Something with printf, and SH the command.
I am not that good with Shell Scripts, but I hope that can lead you into the right direction.

Just one other question, Why do you want to have random terminal colors?
I guess it could be entertaining to open a terminal...
Actually, I will do the same myself!:p

EDIT:

How do you receive user input in bash shell scripts?

---

### Post by Darkness Des on 2010-07-01
Like this.
```

echo -n "O HAI THUR > "
read input
echo "You said $input"

```Or for multiple words,
```

echo -n "Name three colors > "
read color1 color2 color3
echo "You said $color1 $color2 $color3"

```To actually do something with this, just use an "if" function. Makes life a lot easier. I'm assuming you know how to do this.

---

### Post by lkjoel on 2010-07-01
Yes I do.
But how do you get the current location? (such as /home/user/test or /root etc...)
And for the if thing, it is IF, ELIF, and ELSE?

---

### Post by j.bell730 on 2010-07-01
> **lkjoel said:**
> Yes I do.
But how do you get the current location? (such as /home/user/test or /root etc...)
And for the if thing, it is IF, ELIF, and ELSE?

```
pwd
```
Stands for **p**rint **w**orking **d**irectory.

Ifs generally go like this:
```
if [[ "$something" == "something else" ]]
then echo "They are equal."
else echo "They are not equal."
fi
```

[More on if, else, etc.]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_02.html").

---

### Post by lkjoel on 2010-07-02
**UPDATED**
Here is my (dirty) terminal code:
```
#!/bin/bash
quit() {
exit
}
x=6
PATH=$PATH:./
PATH=$PATH:.
while [ x > 5 ]
do
pwdd=$(pwd)
echo -n $pwdd
echo -n " $ "
read command
$command
done
```And I'm not very good at printf.
Could someone tell me how to use printf to make color, and what colors there is?
Thanks!

---

### Post by ibuclaw on 2010-07-02
> **=CrAzYG33K= said:**
> Many thanks for the script, but now I guess I've screwed up my terminal. It wouldn't open up at all anymore..

How do I uninstall it now and come back to the previous state? :o

**EDIT:**

I managed to do the 'uninstall' part coz' luckily I had another Terminal window open somewhere else.
So why did Terminal refuse to open ??

It should be:
```
#!/bin/bash
```
at the top of the file, sorry.

---

### Post by =CrAzYG33K= on 2010-07-02
> **ibuclaw said:**
> It should be:
```
#!/bin/bash
```
at the top of the file, sorry.

Hmm, I'm not getting it to work, I cannot seem to figure out why. Do I need to have only one profile for it to work? Only 'Default' ?

---

### Post by lkjoel on 2010-07-02
The terminal code is just an inch before being perfect.
Everything works, except for the random terminal colors.
If you know how to use printf to make colors, then it is finished.
The terminal code is [here]("http://ubuntuforums.org/showpost.php?p=9538272&postcount=12").

---

### Post by =CrAzYG33K= on 2010-07-02
> **lkjoel said:**
> The terminal code is just an inch before being perfect.
Everything works, except for the random terminal colors.
If you know how to use printf to make colors, then it is finished.
The terminal code is [here]("http://ubuntuforums.org/showpost.php?p=9538272&postcount=12").

I'm not really sure what yer code does. It does look like it does nothing at all. Any explanations? :P

---

### Post by ibuclaw on 2010-07-03
> **=CrAzYG33K= said:**
> Hmm, I'm not getting it to work, I cannot seem to figure out why. Do I need to have only one profile for it to work? Only 'Default' ?

What code are you currently using? Can you paste it here to see?

---

### Post by =CrAzYG33K= on 2010-07-03
> **ibuclaw said:**
> What code are you currently using? Can you paste it here to see?

Never mind, I just figured an easy way out. I just defined some 10 profiles with different fg and bg colors for gnome-terminal and mapped pre-defined (and comfortable) shortcut-keys for them and I'm good to go! :popcorn:

---

### Post by TCHebb on 2010-07-03
Even though you found a way you liked, I still thought I'd post this:

```
#!/bin/bash

PROFILES=( # Change to your profile names
    Default
    Test1
    Test2
)

# Number of elems in the array.
NUM=${#PROFILES[@]}

# Pick a random number
ELEM=$(($RANDOM % $NUM))

# Start gnome-terminal with the chosen profile
exec gnome-terminal --window-with-profile=${PROFILES[$ELEM]}
```It's a small modification to ibuclaw's script, which just uses gnome-terminal's --window-with-profile switch instead of gconftool. Either use his installation instructions, or just put a launcher in a convenient place.

---

### Post by ibuclaw on 2010-07-03
> **TCHebb said:**
> Even though you found a way you liked, I still thought I'd post this:

<snip>

It's a small modification to ibuclaw's script, which just uses gnome-terminal's --window-with-profile switch instead of gconftool. Either use his installation instructions, or just put a launcher in a convenient place.
Yeah ... we discussed that alternate take on IRC immediately after I posted that script.

Oh the secrecy! :P

---

### Post by lkjoel on 2010-07-03
> **=CrAzYG33K= said:**
> I'm not really sure what yer code does. It does look like it does nothing at all. Any explanations? :P
Nothing at all?
It is a Terminal Shell Script, highly customizable, and it has many other cool features.
Here is a walk through.

```
 #!/bin/bash
# for any mac users, making quit to exit is quite hard
quit() {
exit
}
# the x variable is for the forever loop
x=6
# this is a useful feature for windows users,
# because you just need to type script.sh instead of ./script.sh
PATH=$PATH:./
PATH=$PATH:.
# a forever loop
while [ x > 5 ]
do
# pwd=print working directory
pwdd=$(pwd)
# show pwd
echo -n $pwdd
# add the $ symbol
echo -n " $ "
# read the command
read command
# run the command
$command
done
```All that is left is the random terminal colors!

If you want to use it now, copy and paste the code above to a .sh file.
In ~/.bashrc, add these lines at the end:
```
chmod +x /path/to/your/.sh/file
/path/to/your/.sh/file

```I have it installed, and there is not a lot that can convince me to uninstall it.

---

### Post by =CrAzYG33K= on 2010-07-04
> **TCHebb said:**
> Even though you found a way you liked, I still thought I'd post this:

```
#!/bin/bash

PROFILES=( # Change to your profile names
    Default
    Test1
    Test2
)

# Number of elems in the array.
NUM=${#PROFILES[@]}

# Pick a random number
ELEM=$(($RANDOM % $NUM))

# Start gnome-terminal with the chosen profile
exec gnome-terminal --window-with-profile=${PROFILES[$ELEM]}
```It's a small modification to ibuclaw's script, which just uses gnome-terminal's --window-with-profile switch instead of gconftool. Either use his installation instructions, or just put a launcher in a convenient place.

Thanks a lot TCHebb ;)

> **ibuclaw said:**
> Yeah ... we discussed that alternate take on IRC immediately after I posted that script.

Oh the secrecy! :P

lol yeah.

> **lkjoel said:**
> Nothing at all?
It is a Terminal Shell Script, highly customizable, and it has many other cool features.
Here is a walk through.

Thanks man. I appreciate the help. Although, the only thing I didn't understand earlier was this :

```

# run the command
$command
done
```

Now I do! :P

**EDIT:**

There was something similar asked before : [http://superuser.com/questions/41826/color-coated-gnome-terminal](http://superuser.com/questions/41826/color-coated-gnome-terminal)

---

### Post by lkjoel on 2010-07-04
I am glad to know you fixed it!

I am making Terminal Enhancements, and I want to add the Random colored terminal to it.
Could someone explain me how to do this?
Thanks in advance.

Oh and one other minor thing... here is the link to terminal enhancements:P
[http://ubuntuforums.org/showthread.php?t=1523629](http://ubuntuforums.org/showthread.php?t=1523629)

---

### Post by lkjoel on 2010-07-04
Oops! I just changed the contents of this post, since I replied to the wrong thread!
[]("http://ubuntuforums.org/showthread.php?t=1513791")

---

