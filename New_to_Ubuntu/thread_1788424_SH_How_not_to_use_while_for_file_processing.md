---
title: "SH: How not to use while for file processing?"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by frenchn00b on 2011-06-22
Hello, 

This part of code looks like below. While is not a good solution since all variables out of while are not seen / known / remembered by the while function... 

The code:

```

				for each in *.jpg ; do 
					ls -lah "$each"
					FILEN=`date -r "$each" +%F,%H:%M`
					printf "Date modif: $FILEN  ; "
					convert "$each" -resize "$RESOLUTION"  -fill white -undercolor '#00000080' -gravity SouthWest -annotate +0+5 "Date:$FILEN" "/tmp/$each"
					
				
					echo Continuing
				done

```

---

