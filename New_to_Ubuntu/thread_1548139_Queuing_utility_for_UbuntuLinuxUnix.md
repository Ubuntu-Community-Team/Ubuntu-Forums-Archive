---
title: "Queuing utility for Ubuntu/Linux/Unix"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by rhdinah on 2010-08-07
Is anyone familiar with a command line utility that will read from stdin continuously and then spew it out a certain number of seconds later?

For example:

cat file | quefer -t 2 | lastfunct

cats a file, pipes it to this quefer utility upon which two seconds later is re-piped into the program lastfunct.

Of course this could be easily written, but *nix usually has all kinds of handy utilities for the command line.

Thanks for your ideas and info! Peace!:p

-----------------------------------------------------------

Hmmmm ... sounds like I've some programming to do!

---

### Post by rhdinah on 2011-03-02
No replies ... that's okay ... the reason why I was asking this was to buffer stuff for VLC so that video didn't stall when streaming from a server that might just be a bit slow occasionally.

Turns out piping a bunch of *cat*s together and then into VLC with the "-" option to pick up the stream from stdin works. This only works with fast machines. With older machines this solution makes things worse as these *cat*s eat up lots of cycles with their buffering.

The VLC caching policy settings have really never worked for me in this case.

Solution ... make sure files are local ... and on as fast a machine as you can!

---

