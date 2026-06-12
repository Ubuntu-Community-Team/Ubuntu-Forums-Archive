---
title: "Octave and J-Sim"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by ajeannotte on 2009-03-24
The help and installation instructions for J-Sim (the Octave equivalent of Simulink for Matlab) are far above my head and are clearly designed for someone more knowledgeable than myself.

Could someone please to go [http://www.j-sim.org/start.html](http://www.j-sim.org/start.html) and decipher the instructions for someone as linux-simple as myself.

Notes:
- Octave can simply be installed by Add/Remove Programs
- Which package do I need? 
- Where should I be unpacking it?

Any help is greatly appreciated.
Thank you

---

### Post by billgoldberg on 2009-03-24
Yeah, the instructions are a bit hardcore/oldskool.

Make sure you have the required java stuff installed .

Download the program.

Unpack the package to a directory (J-Sim root) .

   2. Set up environment variables J_SIM, CLASSPATH, JAVA_HOME, and IS_UNIX:

	J_SIM=... 	# the J-Sim root 
	CLASSPATH=.:$J_SIM/classes:$J_SIM/jars/tcl.zip:$J_SIM/jars/jython.jar
	JAVA_HOME=... 	# javac and javadoc should be in $JAVA_HOME/bin
	IS_UNIX=... 	# can be anything


Then compile using make in the terminal.

--

That's what they said and without testing it myself (what I won't do) I can't really make it any easier.

Maybe someone who has experience with it will.

Anyway, BUMP

---

### Post by ajeannotte on 2009-03-24
While I appreciate the response, that's exactly what I'm talking about being over my head. 

Any way to dumb that down a little (Absolute-Beginner-Talk-like).

---

### Post by ajeannotte on 2009-03-27
quick bump.... anyone?

---

