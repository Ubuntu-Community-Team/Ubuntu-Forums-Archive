---
title: "Connection Monitor?"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by troyguffey on 2010-09-02
I'm looking for a connection monitor like Mo0's Connection Monitor which shows which program/process has open connections, and how much that connection has/is downloaded.  (Rate might be nice, too)

If it could kill the connection too, that would be good.

I need this because I am on a dial-up connection and it's bandwidth is often fully saturated with no visible indication what program is sucking up all the bandwidth.  (I want to be able to KILL that connection so what *I* consider a priority gets downloaded faster instead of getting the dregs)

---

### Post by Gone fishing on 2010-09-02
will iftop (small commandline runs in terminal quick download over s modem) do what you need, if not ntop would but its rather overkill.

---

### Post by troyguffey on 2010-09-02
> **Gone fishing said:**
> will iftop (small commandline runs in terminal quick download over s modem) do what you need, if not ntop would but its rather overkill.

Tried iftop, but it wasn't what I needed.  It showed every origination as being from my dial-up address instead of the program/process/application.

The ntop website example of output doesn't seem to be what I need either, with the same problem of not showing originating process.

---

### Post by Kellemora on 2010-09-02
Perhaps he meant to say HTop?

Ever since the last couple of updates, I've had to make extensive use of HTop to KILL programs that somehow are still running but FELL OUT OF the GUI so I can't see, access or use them.

If you have the network monitor open in the toolbar and open HTop it's pretty easy to see which program is in it's usage cycle.

It would be better IF the Running Program remained visible in the GUI rather than falling out of it!  
This is a new problem that just started in this past month.
2 years of no problems like this, now it's almost daily.

TTUL
Gary

---

