---
title: "Playing Video From network Drive"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by g_hadgraft on 2008-07-21
Hi i just bought a WD My Book network attached storage drive.  I have been copying files to it however when i try to play videos direct from the NAS the video stutters.  

At first i thought my network wasnt fast enough, it is 54g.  Checking the details i foun it was running at 24 mb/s.  I thought that might not be enough so i tried a test and tested how long it took to copy a 350MB video file which is 40 minutes long.  It took approx 7 minutes to trnasfer it from the NAS to the computer.  

Therefore my thinking is that it should be more than possible to play this direct from the NAS  What would cause the video to stutter when playing from the NAS.

---

### Post by decoherence on 2008-07-21
Copying a file is a fairly fault-tolerant process. If packets need to be resent or get to the destination in the wrong order, it's not a big deal as the TCP stack fixes this stuff automatically.

However if you are playing a video and you have these issues, TCP's error correction will actually compound the hiccups and stuttering, because a video's data needs to be read and displayed in an immediate, sequential fashion.

Some people (real, apple, microsoft) get around this by buffering a few seconds of the video, giving TCP time to work its error-correcting magic while you watch the buffered, uninterrupted video. Of course, if the buffer runs out you get a nice long "rebuffering" wait.

Another way to do this is with streaming software that utilizes UDP to send a stateless video stream. In this case, packets that are dropped are simply ignored. This works well with fast, non-congested networks.

I haven't had much experience setting up either type of these systems... the only reason i know this stuff is because i set up a video editing lab. Depending on the capabilities of your NAS, it may be possible to stream the video with better luck using VideoLAN Client or similar. Hope the information helps you find a specific solution. Let us know!

---

### Post by g_hadgraft on 2008-07-21
Thanks for the tip that worked great.

I didnt realise that error checking would take  so much overhead.

---

