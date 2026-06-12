---
title: "executing a command that waits then runs after a predetermined period of time"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by shortridge11 on 2008-12-14
I want to run a command that will wait 10 seconds then execute. how do i do that?

---

### Post by rlunger on 2008-12-14
You could write a simple looping script just to waste time like so:

    #!/bin/bash
    for a in {1..10000}
    do
    done

Save it, and then make it executable:

    chmod 777 script_name

If the waiting period doesn't have to be exactly 10 seconds, you could play around with the script and get it close...and then run your other command after it like:

    ./wait_script; other_command

Hope that helps.

---

### Post by davec64 on 2008-12-14
Does the command you want to run have a delay switch? Have a look in its MAN pages or -help to see.

You could also use CRON to schedule it, but that might be taking it a bit far, depending what you want to do!

---

### Post by dwasifar on 2008-12-14
Script it using the sleep command.

For more information, at command line type *sleep --help*

edit: actually on second thought you don't even have to get that complicated.  Just add *sleep 10 && * to the beginning of your command.  Say for instance you want to wait 10 seconds then open firefox:

```
sleep 10 && firefox
```

---

### Post by karlr42 on 2008-12-14
Don't busywait, it's not a good idea.

---

### Post by shortridge11 on 2008-12-14
all good suggestions. I think i'll go with sleep. Unless someone knows how to get conky to start 10 seconds after startup without writing a little script.  It's just going to be a startup script.  Weird things happen when i start conky at the beginning of a session.

---

### Post by karlr42 on 2008-12-14
I had the slame problem, with conky not getting drawn properly. I indeed used sleep.

---

### Post by laffinet on 2008-12-14
That's a known issue. From memory I think it's got to do with compiz, so you want to make sure that compiz is started before conky is loaded. Most people use a little start up script. Mine looks like this:

```
#!/bin/bash
sleep 20 && conky;
```

---

