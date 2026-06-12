---
title: "Does this sound like standard teminal?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by wbest on 2009-07-17
This is a kind of weird question...so I'm sorry if I put it in the wrong place, feel free to move it (if you have admin rights).
 
So its a long story about why I need to know this (I'll tell you if you must know) but do these statements sound like they describe a normal terminal (no special shells, just out-of-the-box ubuntu terminal)?
 
Echoing of keyboard input to the active screen buffer 
Line input, in which a read operation does not return until the ENTER key is pressed 
Automatic processing of keyboard input to handle carriage returns, CTRL+C, and other input details 
Automatic processing of output to handle line wrapping, carriage returns, backspaces, and other output details

---

### Post by manuelb on 2009-07-17
It sounds *a lot* like a somewhat technical description of a normal terminal: obviously, technicalities are for those who grasp them but indeed, should the question be "describe a unix-like terminal in 4 lines", you came up with a nice one ;)

---

### Post by jonobr on 2009-07-17
Yeah, Id like the long explanation:-)

Isnt this all supported in a standard terminal window anyway?
Is this a trick question?

---

### Post by manuelb on 2009-07-17
> **jonobr said:**
> Yeah, Id like the long explanation:-)

Interesting indeed, +1 for me!

---

### Post by iamkrazee on 2009-07-17
I bet you're writing your own terminal. For school project maybe. lol. I had the same project. :P

---

### Post by wbest on 2009-07-17
Okie-day, the long explanation it is.
 
I'm working on porting Windows code to Linux.  It's for work, and I'm just an intern so I'm not totally clear on all the little intricacies and such.  Anyway, so right now I'm working on a program that uses console.  The program sets two things in console:
 
ENABLE_ECHO_INPUT
ENABLE_PROCESSED_INPUT
 
With some searching, I came across the msdn site that describes High-Level Console I/O, which covers both of the above calls.
So I needed to make sure Terminal could do something roughly equivalent to the above calls; and I set out to figure out if Terminal acts, for the most part, like High-Level Consonsole in Windows.
 
I went into the description of High-Level Console to see if it roughly resembles standard terminal.  I will also provide a bit more for your judgement.
 
All of the following console input modes are enabled for a console's input buffer when a console is created:

[LIST]
[*]Line input mode
[*]Processed input mode
[*]Echo input mode
[/LIST]Both of the following console output modes are enabled for a console screen buffer when it is created:

[LIST]
[*]Processed output mode
[*]Wrapping at EOL output mode
[/LIST] 
On the subject of ENABLE_ECHO_INPUT and ENABLE_PROCESSED_INPUT:
ENABLE_ECHO_INPUT
Used with a console input handle to cause keyboard input read by the [**[COLOR=#0033cc]ReadFile[/COLOR]**]("http://msdn.microsoft.com/en-us/library/aa365467(VS.85).aspx") or [**[COLOR=#0033cc]ReadConsole[/COLOR]**]("http://msdn.microsoft.com/en-us/library/ms684958(VS.85).aspx") function to be echoed to the active screen buffer. Characters are echoed only if the process that calls **ReadFile** or **ReadConsole** has an open handle to the active screen buffer. Echo mode cannot be enabled unless line input is also enabled. The output mode of the active screen buffer affects the way echoed input is displayed.
 
ENABLE_PROCESSED_INPUT
Used with a console input handle to cause the system to process any system editing or control key input rather than returning it as input in the read operation's buffer. If line input is also enabled, backspaces and carriage returns are handled correctly. A backspace causes the cursor to move back one space without affecting the character at the cursor position. A carriage return is converted to carriage return – linefeed character combination. If echo input mode is enabled and the output should reflect system editing, processed output must be enabled for the active screen buffer. If processed input is enabled, the CTRL+C key combination is passed on to the appropriate handler regardless of whether line input is enabled. For more information about control handlers, see [[COLOR=#0033cc]Console Control Handlers[/COLOR]]("http://msdn.microsoft.com/en-us/library/ms682066(VS.85).aspx").

---

