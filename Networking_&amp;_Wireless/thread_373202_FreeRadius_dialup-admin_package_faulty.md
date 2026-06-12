---
title: "FreeRadius dialup-admin package faulty??"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by (aptainMorgain on 2007-03-01
Hey guy's,
I did a "apt-get" on FreeRadius and Dialup-Admin yesterday and everything went
very smoothly until after the installation. When I wanted to create some new groups
in Dialup-Admin, it didn't show up when I went over to the "Show Groups" section.

It created all the info under the "radgroupreply" table, but nothing under "usergroup".
It was as if it just wasn't running the "INSERT INTO....usergroup...." command.

Having done the install from the FreeRadius tar file the day before and having this
part (the only part :-? ) actually working, I decided to just copy and over write the
existing relevant .php files and voala - it's working.

Now I'm kinda new to the community / Linux Ubuntu and have no clue as to how or
even if I should tell anybody about it. I'm thinking Mark might not have time to have
a look at this thread, but I'm sure somebody out there would like to know that this
anomaly has occurred and that should there be repetitive occurrences, will need to be
dealt with accordingly :) 

I hope this snowball's into somebody's assistance in the near future  ):P

---

