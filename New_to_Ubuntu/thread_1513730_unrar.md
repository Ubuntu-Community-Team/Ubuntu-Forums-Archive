---
title: "unrar"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-06-19
I am trying to unrar a file, I have downloaded unrar from the software center, and from a terminal window... now what?  I see no way of using it, it's not in accessories, if I click on the file, I have no unrar options even if I use the open using another application option.  I really like ubuntu, but man, it's kinda confusing sometimes

thanks in advance
beelzebufo

---

### Post by karthick87 on 2010-06-19
You should install the following to unrar a file,


```
sudo apt-get install rar
```

---

### Post by Primefalcon on 2010-06-19
like most other programs just open the ubuntu software center

type in what you want in the search box (in this case rar)

install RAR

done

you will now be able to right click and extract

---

### Post by beelzebufo on 2010-06-20
dag nabbit, tried both ways and still nothing, when I search for unrar or rar I only get a text file like this

# unrar(1) completion by Guillaume Rousse <rousse@ccr.jussieu.fr>

have unrar &&
_unrar()
{
    local cur

    COMPREPLY=()
    cur=`_get_cword`

    case "$cur" in
        -*)
        COMPREPLY=( $( compgen -W '-ad -ap -av- -c- -cfg- -cl -cu \
            -dh -ep -f -idp -ierr -inul -kb -o+ -o- -ow -p -p- -r -ta \
            -tb -tn -to -u -v -ver -vp -x -x@ -y' -- "$cur" ) )
        ;;
        *)
        if [ $COMP_CWORD -eq 1 ]; then
            COMPREPLY=( $( compgen -W 'e l lb lt p t v vb vt x' -- "$cur" ) )
        else
            _filedir '@(rar|RAR)'
        fi
        ;;
    esac

    return 0
} &&
complete -F _unrar $filenames unrar

# Local variables:
# mode: shell-script
# sh-basic-offset: 4
# sh-indent-comment: t
# indent-tabs-mode: nil
# End:
# ex: ts=4 sw=4 et filetype=sh

:confused:
totally confussed
thanks again
beelzebufo

---

### Post by jocko on 2010-06-20
unrar is a command-line program. To use it type this in a terminal:
```
cd [COLOR=Blue]/path/to/folder[/COLOR]
unrar e [COLOR=Blue]filename.rar[/COLOR]
```
Where [COLOR=Blue]/path/to/folder[/COLOR] is the folder the file is in, and [COLOR=Blue]filename.rar[/COLOR] is the name of the file.

But there's an easier way:
Once you have installed unrar, file-roller can extract .rar for you. Right click the file and select "extract here" in the menu.

---

### Post by beelzebufo on 2010-06-20
aha, thanks man

---

### Post by alphacrucis2 on 2010-06-20
> **beelzebufo said:**
> aha, thanks man

If you want file roller to appear in the menu. Then System - Preferences -Main Menu, Select Accessories and tick the check box beside archive manager.

---

