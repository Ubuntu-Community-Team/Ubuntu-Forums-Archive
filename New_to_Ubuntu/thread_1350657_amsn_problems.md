---
title: "amsn problems"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by jrandolph on 2009-12-09
So i am curious if anyone can possibly explain what the problem is with my amsn
ok so first off i use amsn because of the cam support
but everytime that I try to log into it - amsn stalls and uses 100%cpu
but I can log in with another user name and it works just fine
and prior to it locking up alltogether the past few day i get error messages - I tried to report them but when i explain my problem and click report it locks up
could it possible be something wrong with my msn account?
I just dont see how this is possible
I can try to give further details if its possible
I have uninstalled and reinstalled but i dont think that it ever fully uninstalls it
sorry this is so long - hard to keep short

thanks
Jacob

---

### Post by kelvin spratt on 2009-12-09
Remove the MSN folders in your home folder you might have to click on view hidden files 1st, 
Then restart MSN and set it up again.

---

### Post by jrandolph on 2009-12-09
ok so that solved the problem with it locking up but i still get error messages when i log in 

Here is the errors that i get 

too many nested evaluations (infinite loop?)
    while executing
"string tolower $locale"
    (procedure "::tcl::clock::format" line 7)
    invoked from within
"clock format [clock seconds] -format %H:%M:%S"
    (procedure "timestamp" line 2)
    invoked from within
"timestamp"
    (procedure "::pluginslog::plugins_log" line 15)
    invoked from within
"::pluginslog::plugins_log $plugin $msg"
    (procedure "plugins_log" line 4)
    invoked from within
"plugins_log core "Calling event $event with variable $var\n""
    (procedure "::plugins::PostEvent" line 4)
    invoked from within
"::plugins::PostEvent parse_contact evpar"
    (procedure "::abook::setVolatileData" line 24)
    invoked from within
"::abook::setVolatileData $contact PSM $psm"
    (procedure "::NS::Snit_methodhandleUBX" line 34)
    invoked from within
"$self handleUBX $command $payload"
    (procedure "::NS::Snit_methodhandleCommand" line 72)
    invoked from within
"$options(-name) handleCommand $command $payload"
    (procedure "::Connection::Snit_methodreceivedData" line 111)
    invoked from within
"ns receivedData"

---

