---
title: "Acitvity Journal is blank for non-root user"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by robinparriath on 2010-06-26
Hi everyone,

I installed the Gnome-activity journal, but it's not showing anything in it.

I checked to see if Zeitgeist is running and I find two processes running:

zeitgeist-daemon and zeitgeist datahub.

I tried restarting zeitgeist-daemon from the terminal by 
$ zeitgeist-daemon --quit
$ zeitgeist-daemon

Here's what I get:

> DEBUG:zeitgeist.engine:daemon is configured to run with these extensions: ['_zeitgeist.engine.extensions.blacklist.Blacklist', '_zeitgeist.engine.extensions.datasource_registry.DataSourceRegistry']
INFO:zeitgeist.sql:Using database: /home/robin/.local/share/zeitgeist/activity.sqlite
DEBUG:zeitgeist.sql:Core schema is good. DB loaded in 2.82406806946ms
DEBUG:zeitgeist.extension:Loading extension 'Blacklist'
DEBUG:zeitgeist.blacklist:No existing blacklist config found
DEBUG:zeitgeist.extension:Loading extension 'DataSourceRegistry'
DEBUG:zeitgeist.datasource_registry:Loaded data-source data from /home/robin/.local/share/zeitgeist/datasources.pickle
DEBUG:root:Checking for another running instance...
DEBUG:root:No running instances found.
INFO:root:Starting Zeitgeist service...

and it's stuck there.

When I sudo the same commands, it captures only what I did as root and that's not I want in my activity journal.

Am I missing something? :confused:

---

### Post by chunky bacon! on 2011-04-19
Bump.

Same issue here.

Ignore bump:  I guess it needed to actually index something (doh).  I didn't have an understanding of how the product worked, sorry.

---

