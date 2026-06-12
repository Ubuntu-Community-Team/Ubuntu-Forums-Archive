---
title: "bash: bad flags"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by rutledmj on 2009-10-01
i was wondering if someone could find the error in this code.  the error occurs when an invalid flag is used.  instead of printing "invalid flag" like i want it to, it doesn't print anything.  All other flag options work except invalid ones.  

```
CheckOpts2()
        {
        OPTIND=1
        optionLetters="$1"
        shift
        args="$@"
        status=0
        while : ; do
                getopts ":$optionLetters" optLetter $args
                status=$?
                [ $status != 0 ] && break;              
                if [ "$optLetter" = '?' ] ; then
                        status=1
                        break;
                fi
                eval flag_$optLetter=-$optLetter
        done
        return $status
        }

CheckOpts2 "sm " "$@"

if [ -n "$flag_m" ] ; then

        echo Flag m is on.

elif [ -n "$flag_s" ] ; then

        arg2=$2
[INDENT]echo flag is s $arg2
[/INDENT]elif [ -n "$flag_ " ] ; then

        arg2=$1
[INDENT]echo flag is blank $arg2
[/INDENT]else

        echo invalid flag.

fi
```

---

### Post by Captain_tux on 2009-10-02
I think you'd get better assistance if you were to post this in the programming forum...

---

### Post by scorp123 on 2009-10-02
> **rutledmj said:**
>  ```
 if [ -n "$flag_m" ] ; then

        echo Flag m is on.

elif [ -n "$flag_s" ] ; then

        arg2=$2
[INDENT]echo flag is s $arg2
[/INDENT]elif [ -n "$flag_ " ] ; then

        arg2=$1
[INDENT]echo flag is blank $arg2
[/INDENT]else

        echo invalid flag.

fi
``` Why not use the "case" statement? It would be more elegant and probably work better.

```
...
case "$flag" in
  m)
     echo "Flag is m ..." || exit 1
     ;;
  s)
     echo "Flag is s ..." || exit 1
     ;;
  *)
     echo "Flag was invalid."
     exit 1
esac

```

---

