---
title: "Shell scripting for a total noob"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by ptrakk on 2011-06-19
making a way to open mp3's in xmms2 to learn the sh script
here's my code 

#!/bin/bash

 x=$( pwd )
 x2=$( echo $x/$1 )
 x3=$( echo $x2 | sed 's/ /\\ /g')
 x4=$( echo xmms2 add $x3 )
 xmms2 stop 
 xmms2 clear 
 $x4  <----------(CRASHES HERE.)-(ERROR: Invalid url: 6\)
 echo $x4 <--(when i paste the output into the terminal it works)
 xmms2 play


basically i think it runs $x4 as "xmms2 add $x3"
      .:And:. 
xmms2 doesn't know how to add a variable into the playlist.

Is there a way to convert $3 to plaintext and put it into the command before xmms runs it?

+5 internets to whoever can help!

---

### Post by Vaphell on 2011-06-19
is there any particular reason why you do that sequence of echos captured to serve as variables down the road?

```
#!/bin/bash

xmms2 stop
xmms2 clear
xmms2 add "$PWD"/"$1"
xmms2 play

```

$PWD and $1 variables are put in double quotes to prevent segmentation on spaces which i assume you wanted to achieve with that sed line.

---

### Post by ptrakk on 2011-06-21
> **Vaphell said:**
> is there any particular reason why you do that sequence of echos captured to serve as variables down the road?

```
#!/bin/bash

xmms2 stop
xmms2 clear
xmms2 add "$PWD"/"$1"
xmms2 play

```

$PWD and $1 variables are put in double quotes to prevent segmentation on spaces which i assume you wanted to achieve with that sed line.


thanks! you are awesome! now how to mark as solved!

---

