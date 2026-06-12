---
title: "Help writing scripts"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Defiant Rat on 2009-12-10
I'm writing a script to install some programs. I want to give the user the option to find out more about the program before they install it, by opening the homepage (unless anyone knows a better way). This is what ive got:
```
echo -n "Install program? (y/n) If you want more information about the program type s > "
read
if [ "$REPLY" = "y" ]; then
    echo "Installing program"
    
elif [ "$REPLY" = "s" ]; then
    echo "Firefox will now open the program homepage"
    echo "Install program? (y/n) >"
    read
    if [ "$REPLY" = "y" ]; then
        echo "Installing program"
        
    elif [ "$REPLY" = "n" ]; then
    echo "Program will not be installed"
else
    echo "Program will not be installed"
fi
```But, when i run it i get:
```
line 21: syntax error: unexpected end of file
```What do i need to change?

Thanks

---

### Post by spillin_dylan on 2009-12-10
> **Defiant Rat said:**
> I'm writing a script to install some programs. I want to give the user the option to find out more about the program before they install it, by opening the homepage (unless anyone knows a better way). This is what ive got: 
<snip>
```
echo -n "Install program? (y/n) If you want more information about the program type s > "
read
if [ "$REPLY" = "y" ]; then
    echo "Installing program"
    
elif [ "$REPLY" = "s" ]; then
    echo "Firefox will now open the program homepage"
    echo "Install program? (y/n) >"
    read
    if [ "$REPLY" = "y" ]; then
        echo "Installing program"
        
    elif [ "$REPLY" = "n" ]; then
    echo "Program will not be installed"
    [COLOR="Red"]fi[/COLOR]
else
    echo "Program will not be installed"
fi
```
I think you forgot to close one "if" statement.  Highlighted in red.

---

### Post by Defiant Rat on 2009-12-10
> **spillin_dylan said:**
> <snip>
```
echo -n "Install program? (y/n) If you want more information about the program type s > "
read
if [ "$REPLY" = "y" ]; then
    echo "Installing program"
    
elif [ "$REPLY" = "s" ]; then
    echo "Firefox will now open the program homepage"
    echo "Install program? (y/n) >"
    read
    if [ "$REPLY" = "y" ]; then
        echo "Installing program"
        
    elif [ "$REPLY" = "n" ]; then
    echo "Program will not be installed"
    [COLOR=Red]fi[/COLOR]
else
    echo "Program will not be installed"
fi
```I think you forgot to close one "if" statement.  Highlighted in red.

Thanks, i thought i'd tried that but obviously not #-o

cheers :)

---

