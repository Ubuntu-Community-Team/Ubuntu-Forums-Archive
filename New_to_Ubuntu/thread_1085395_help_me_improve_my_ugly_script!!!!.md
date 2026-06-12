---
title: "help me improve my ugly script!!!!"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by jmd9qs on 2009-03-03
hi all,

i am just getting in to bash scripting, so don't be too harsh... 

i've created this little backup script, and it's just awfull... ugly, doesn't work like I want it to, the works. anyways, i was hoping some of you might help me improve it and learn a little in the process.

what i wanted to do:
1. interactively take a filename (from user input) to backup w/ tar
   1a - if the file wasn't present, or no input, exit
2. interactively take a "save path" (from user input) to save to
   2a - if there isn't a directory w/ that name, or no input, exit
3. tar the $filename to the $savepath with a $timestamp filename

so far, i have this:

```
#!/bin/bash
#

##### Constants

FILENAME=
SAVEPATH=
TITLE="Hello $USER! Let's back something up!"
TIMESTAMP="$(date +"%m-%d-%Y")"
DIR_TREE="$(dir)"
SELECTION=
PWD="$(pwd)"


##### Functions

function dir_tree
{
        echo "$TITLE"
        echo ""
        echo " You are here: $PWD"
        echo "These are the Files/Directories in $PWD"
        echo "$DIR_TREE"
}

function press_enter
{
        echo ""
        echo -n "Please press Enter to continue:  "
        read
        clear
}

##### Main

until [ "$SELECTION" = "n" ]; do
 echo ""
        dir_tree
        echo ""
        echo ""
        echo "What would you like to backup? >  "
        read FILENAME
        if [ "$FILENAME" = "\ " ]; then
                exit 1;
        fi
        echo ""
        echo ""
        echo "Where would you like the new .tar.gz archive for $FILENAME stored? (just specify directory, filename is automatic) >  "
        read SAVEPATH
        if [ "$SAVEPATH" = "\ " ]; then
                exit 1;
        fi
        echo
        echo "O.K. - so you want to archive $FILENAME  to $SAVEPATH ? (y for yes, n to quit) >  "
        read SELECTION
        case $SELECTION in
                y ) tar -cjvf "$SAVEPATH$TIMESTAMP-of-$FILENAME.tar.gz" $FILENAME; exit;;
                n ) exit;;
                * ) echo "Invalid character... Please type in y or n to continue"; press_enter;;
        esac
done

```

for reasons unknown (to me :( ) the "program" won't exit if no input is selected, and I haven't figured out how to do it if the file/directory doesn't exist.

any help folks?

---

