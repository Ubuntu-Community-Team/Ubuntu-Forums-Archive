---
title: "TVTime sox instance closing using shell script."
date: 2009-07-06
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2009-07-06
Hi,

   I'm using 'TVTime' for watching TV in Ubuntu 8.04 LTS, I had problem in sound when I used TVTime, problem was sound was not coming. While searching through internet I got a solution using 'sox' . But I need to execute sox with some parameter parallel with TvTime for that I created one sh file. The problem, I'm facing is when I close TvTime using the close button still the instance of sox will be running in background because of that I will not be able to play any music files (Like mp3 or any videos). If I close this  instance manually I can able to here the sound of mp3. Anyone help me on this, I want a script itself I could able to close this instance while I close the TvTime. 


Please help me on this. 

Regards,
Vipin Balakrishnan.

---

### Post by sisco311 on 2009-07-06
```
#!/bin/bash

#run tvtime in the background
tvtime&

#if sox is not running, then start it in the background
if [ ! $(pidof sox) ]; then
  sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
fi

#kill sox when tvtime is closed
wait $(pidof tvtime)
killall sox

exit 0
```

---

### Post by vipin.balakrishnan on 2009-07-06
Hi sisco311,

 Thank you very much, It is working very fine.

Regards,
Vipin Balakrishnan

---

