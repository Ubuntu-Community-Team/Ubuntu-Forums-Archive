---
title: "bash command help"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by ALF102 on 2010-09-07
I've just got this bash command for downloading mangas.

#!/bin/bash
for  i in `seq -f"%03g" 031 056`
do
    wget -c "http://s1-a.animea-server.net/2944%2F2_VHXLV%2Fkankei01_$i.jpg"
done

now, what must I modify in the  bash command so that I can specify a download directory and if possible also renaming all the files by numbers.

EDIT: nvm, it seems I can do it by cd to the directory i want the files to be downloaded and then run the script

---

