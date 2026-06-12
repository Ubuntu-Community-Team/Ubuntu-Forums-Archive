---
title: "Shell Script Help"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by TheAJGman on 2011-05-25
Im in the process of making an automated script I just need some help. I need commands that:
give you an option like goto: in windows
that let you enter a variable into a command

---

### Post by yeats on 2011-05-25
Not sure if this is what you mean, but if you're trying to get input from the user and store it in a variable, you can do:

```
read -p "What is your first name?" FIRST_NAME
echo "Hello, $FIRST_NAME!"
```

Is that what you mean?  "Goto" in BASIC is not the same thing as this, so I may be misunderstanding your question ;-).

---

### Post by TheAJGman on 2011-05-25
yes to the first but i also need some thing like an ABC option were you enter A for choice one B for two etc.

---

### Post by matt_symes on 2011-05-25
Hi

For goodness sake, don't use the goto statement in any programming language unless you have absolutely no choice. That is a bad bad bad habit to get into.

Use functions. Have a look at this.
```

#!/bin/bash

function function_a
{
    echo "You entered a"
}

function function_b
{
    echo "You entered b"
}

function function_c
{
    echo "you entered c"
}

function function_un
{
    echo "you entered something unknown"
}

read -p "Enter option :" OPTION

case "$OPTION" in
    a)
        function_a ;;
    b)
        function_b ;;
    c)
        function_c ;;
    *)
        function_un ;;
esac

```It's only very basic but you get the general idea. Copy and paste it into gedit. Save it and run it from a terminal. Add some error handling and adapt to your needs.

Kind regards

---

### Post by TheAJGman on 2011-05-25
??????? I just need 4 choices to run 4 different commands. So if someone types x86_generic it runs
BOARD=x86-generic
If I they type arm_generic it runs
BOARD=arm-generic

---

### Post by matt_symes on 2011-05-25
Hi

> ??????? I just need 4 choices to run 4 different commands. So if someone types x86_generic it runs
BOARD=x86-generic
If I they type arm_generic it runs
BOARD=arm-generic

Use the case statement then, as i have shown, if you don't require fully blown functions and set your variables there. 

Unless i am misunderstanding what you require, I'm not quite sure why you can't do something like

```
#!/bin/bash

BOARD=
while [[ "$BOARD" != "x86-generic" && "$BOARD" != "arm-generic" ]]
do
        read -p "enter option: " BOARD
done

echo "end"
```

to get the input into BOARD and perform error checking on what they type. This can all be performed in a loop.

Seriously, any developer will tell you goto's create spaghetti code. You don't need them.

Kind regards

---

### Post by ApOgEEs on 2011-05-25
> **TheAJGman said:**
> ??????? I just need 4 choices to run 4 different commands. So if someone types x86_generic it runs
BOARD=x86-generic
If I they type arm_generic it runs
BOARD=arm-generic

Hi,

Here is an example:
```

#!/bin/bash

echo "Type 'x86_generic' for x86-generic"
echo "Type 'arm_generic' for arm-generic"
echo "Type 'op_3' for option-3"
echo "Type 'op_4' for option-4"

read -p "Select your board: " myInput

case "$myInput" in
        "x86_generic")
                BOARD="x86-generic";;
        "arm_generic")
                BOARD="arm-generic";;
        "op_3")
                BOARD="option-3";;
        "op_4")
                BOARD="option-4";;
        *)
                BOARD="unknown";;
esac

echo "Your selected board is" $BOARD


```

I would agree with matt_symes, you can use function to replace goto. There is no goto statement in bash.

---

### Post by TheAJGman on 2011-05-26
Thanks I was a bit confused because the languages are simmilar so I thought you could do something like if bla goto A but no I cant

---

### Post by yeats on 2011-05-26
You might benefit from walking through this guide:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by matt_symes on 2011-05-26
Hi

> **yeats said:**
> You might benefit from walking through this guide:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

I also have 2 very good links for bash programming in my signature at the moment. Both sites come highly recommend by others, including sisco311; a high calibre script writer and a member of these forums.

Kind regards

---

### Post by TheAJGman on 2011-05-26
ok i need some more help. i need to run
```
BOARD=x86-generic
./setup_board --board=${BOARD}
./set_shared_user_password.sh
```
after running
```
./make_chroot
./enter_chroot.sh
```
in an sh file but when i enter chroot the rest of the commands don't run

---

### Post by TheAJGman on 2011-05-27
Ok I screwed up. I was expanding my main ubuntu partition when 90% through moving files the power went out now it won't boot. Help

---

### Post by TheAJGman on 2011-05-27
Nevermind I'm just gonna reinstall

---

### Post by ApOgEEs on 2011-05-27
well, good luck!

---

### Post by TheAJGman on 2011-05-27
got ubuntu working. now i need to run a command
```
./build_image --board=${BOARD} --withdev --noenable_rootfs_verification
```
inside chroot
```
./enter_chroot.sh
```
how do i make it so that just that command runs in chroot.

---

### Post by TheAJGman on 2011-05-28
i need a command that will only list the user name like
blabla@user-pc:~$ some command
blabla
blabla@user-pc:~$

---

### Post by ApOgEEs on 2011-05-28
> **TheAJGman said:**
> i need a command that will only list the user name like
blabla@user-pc:~$ some command
blabla
blabla@user-pc:~$

Try this command...
```
$ whoami

```

---

