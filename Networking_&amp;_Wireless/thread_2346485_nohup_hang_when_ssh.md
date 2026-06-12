---
title: "nohup hang when ssh"
date: 2016-12-15
forum: Networking &amp; Wireless
---

### Post by octlie on 2016-12-15
Dear All, 

Weird problem. 

I connect to a Ubuntu remote server (say 'server') from by windows client via a putty.exe ssh protocol with the defaults (in a script, say 'BuildCmd') to execute a set of commands in a matlab script ('base0'): 

Cmd= BuildCmd('make -p 'certain dir'); 
system(Cmd);
...
Cmd= BuildCmd(' cd 'that dir'; nohup 'some command' >& output.txt &'); 
system(Cmd);
...

If I run the 'base0' the 1st time, I get a hang at the nohup command (does not get into the background, and I get stuck at that code line. None of the ^z, bg; ~. and few other options to move nohup to the background that I saw on the forum have worked. Curious enough, if I terminate the hanged script and rerun the 'base0' again (when the 'dir' is already created and 'make -p' does not do much), all goes well, nohup gets backgrounded and 'base' progresses.

 If I modify the 'base' (say 'base1') by adding as 1st/2nd lines:

Cmd= BuildCmd('rm -r ' that dir'); 
system(Cmd);
 
I get a hang at nohup whether I run the 'base1' anew or rerun it. 
I think the reason the 'base0' works on termination/rerun but not 'base1' is that with the 1st 'base0' run, while nohup gets hang and foregrounded, the 'make -p 'dir'' on rerun does not kill the 1st nohup, and when the 2nd nohup is issued, the 1st gets killed or backgrounded, and the 2nd gets backgrounded (which I want to) ok for some reason. 
With 'base1', the 'dir' is removed with the rerun, killing the 1st hang nohup, and when the 2nd nohup is issued, again gets stuck in the foreground. 

Any suggestions (other than screen/ timux)?

Thank you, 

Octavian

---

