---
title: "Could this work code work?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by HACKER1993 on 2009-03-02
I have just finished this code I know its short its my first working code but it is the basis of making a tar ball and installing it hopefully it works haven't tested it yet but would like the community to look over it and point out any flaws
[PHP] #!/bin/sh
# Hacker1993
# script for untaring a tarball

tar zxvf- input_file="`zenity --file-selection`"
cd input_file="`zenity --file-selection`"
./configure
make
sudo make install
[/PHP]

Thanks

---

### Post by snova on 2009-03-02
> **HACKER1993 said:**
> [PHP]tar zxvf- input_file="`zenity --file-selection`"[/php]

That won't work. It would expand to something like

[php]tar zxvf input_file=/home/user/Desktop/tarball.tar.bz2[/php]

And no further. This would:

[PHP]tar zxvf "`zenity --file-selection`"[/PHP]

Also, what is the point of **v**? You can't see the output.

> [PHP]cd input_file="`zenity --file-selection`"[/php]

That won't either, for similar reasons.

[php]cd "`zenity --file-selection --directory`"[/php]

It'd be nice if this would auto-detect the directory name (usually it's the same as the tarball's filename, minus the extension), but I don't know of an easy way to separate the extension. And it's not always correct, either.

> [PHP]sudo make install[/php]

sudo will ask for your password in the terminal, which presumably won't even exist. gksudo will work, however:

[PHP]gksudo make install[/PHP]

Probably the biggest flaw overall is the lack of visual feedback. If anything goes wrong (frequent), or just takes a while (most do), there's no indication of progress.

---

