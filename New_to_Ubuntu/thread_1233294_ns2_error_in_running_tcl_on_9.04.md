---
title: "ns2 error in running tcl on 9.04"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by yasirimteyaz on 2009-08-06
Hi,everyone.
I got a problem about running NS2 (2.33) on Ubuntu 9.04.
It got installed successfully without any errors.
I set-up all the PATHS.
after $ ns, i am getting the % sign
but when I enter the "ns simple.tcl" command ,the shell show this error below:

[COLOR="Purple"]
$ns simple.tcl[/COLOR]
[COLOR="DarkOrchid"](_o5 cmd line 1)
invoked from within
"_o5 cmd at 1 “puts “Hello World!””"
invoked from within
"catch "$self cmd $args" ret"
invoked from within
"if [catch "$self cmd $args" ret] {
set cls [$self info class]
global errorInfo
set savedInfo $errorInfo
error "error when calling class $cls: $args" $..."
(procedure "_o5" line 2)
(SplitObject unknown line 2)
invoked from within
"_o5 at 1 “puts “Hello World!””"
("eval" body line 1)
invoked from within
"eval $scheduler_ at $args"
(procedure "_o3" line 3)
(Simulator at line 3)
invoked from within
"$ns at 1 “puts \“Hello World!\””"
(file "simple.tcl" line 2)[/COLOR]



did anyone come across with the same problem?
If anyone know,could you help me.
thank you

---

