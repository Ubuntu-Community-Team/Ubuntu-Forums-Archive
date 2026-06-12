---
title: "Conky and Amarok"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by AdamMPkins on 2010-04-17
I've followed the advice listed in various other sources I found via google sources. I have created an amarok script file saved in .conky and made it executable . It is as follows:
```
#!/bin/bash
# based on: amaroK info display script by eirc <eirc.eirc@gmail.com>
# amarok2 info display script by fireandfuel <fireandfuel@hotmail.de>
#
# requirements: amaroK 2 (!)

case “$1&#8243; in

# Now Playing Info
artist) qdbus org.kde.amarok /Player GetMetadata | grep artist ;;
title) qdbus org.kde.amarok /Player GetMetadata | grep title ;;
album) qdbus org.kde.amarok /Player GetMetadata | grep album ;;
year) qdbus org.kde.amarok /Player GetMetadata | grep year ;;
genre) qdbus org.kde.amarok /Player GetMetadata | grep genre ;;

esac
```


I call upon it in my .conkyrc file with:
```

Music ${hr 2}

${execi 10 ~/.conky/amarok artist}
${execi 10 ~/.conky/amarok title}
${execi 10 ~/.conky/amarok album}
${execi 10 ~/.conky/amarok year}
${execi 10 ~/.conky/amarok genre}
```

After all of this, I see the heading for the music section but nothing else. Any help getting the now playing info displayed?

---

### Post by AdamMPkins on 2010-04-17
Anybody have any assistance they can offer?

---

### Post by AdamMPkins on 2010-04-18
If anyone has anything to offer, I'd really appreciate it. If other information is needed, please let me know.

---

