---
title: "how to pass argument from java to shell script"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by shishir_knit on 2009-04-11
i hav written a java code:

     String[] l={"10","20"};
     Process proc = Runtime.getRuntime().exec("./cp.sh ",l);

program is compiling successfully.
but how can i access the parameter send from java in shell script

please give the code for shell script

---

### Post by lfaraone on 2009-04-11
The first argument is $1, second is $2, etc. 

See [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-pass-command-line-parameter-to-shell-script-254396/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-pass-command-line-parameter-to-shell-script-254396/)

---

