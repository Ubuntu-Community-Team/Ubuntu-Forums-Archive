---
title: "ls colors in Term - default"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by gmgj on 2010-02-19
Is there a chart somewhere that shows the default colors used.  

The man pages say the environment variable LS_COLORS and dircolors are involved.
  
[I] LS_COLORS='rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:'
[/I]

This looks like a mix of things like 'rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=4filetypes ..' and filetypes

Is there a script or a program that would read the environment variable LS_COLORS and display something like  

rs  denotes an rs directory?  [COLOR="SandyBrown"]xxxxxx[/COLOR]
ex  executable            [COLOR="Green"]xxxxxx[/COLOR]


if there is not way to display something like this, can someone help me decode it?

Can you output color coded output from s shell script?

---

### Post by Tibuda on 2010-02-19
try this:
```
a=' '
for c in `dircolors -p | cut -d'#' -f1 | grep -v '^ *$'`; do
    if [[ "$c" =~ ^([0-9]*;?[0-9]+)$ ]]; then
        echo -en "\033[${c}m${a}\033[0m "
    else
        a=$c
    fi
done
```

EDIT: this will use the LS_COLORS variable instead of dircolors output:
```
a=' '
for c in `echo $LS_COLORS | sed 's/[=:]/ /g'`; do
    if [[ "$c" =~ ^([0-9]*;?[0-9]+)$ ]]; then
        echo -en "\033[${c}m${a}\033[0m "
    else
        a=$c
    fi
done
```

EDIT: The first of this script didnt worked on bash, only in zsh. I have fixed it.

---

