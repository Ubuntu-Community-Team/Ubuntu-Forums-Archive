---
title: "KSH - script not running"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by eluzi on 2009-01-15
I've got a script, called ideploy_wrap.sh, to run with KSH that looks like this:

#!/usr/bin/ksh
#set -x
program_dir=`dirname $0`
cd ${program_dir}
. ${program_dir}/ideploy.inc
#########################################
etc
etc
etc

The automatic installer tries to run it and receives the following error:

No such file or directory

Since I don't know exactly what is the command that it uses to run the script I tried running it manually and received the same error. I tried:

sh ideploy_wrap.sh
./ideploy_wrap.sh
/ideploy_wrap.sh
/bin/ksh ideploy_wrap.sh
and so on...

Both with bash and ksh, and it still didn't work.

I've got KSH in /usr/bin and /bin. 

To check if KSH was working I tried a script like this:

#!/usr/bin/ksh
# set -x
ls -l

And it worked fine...

Any ideas ?

---

### Post by cmnorton on 2009-01-16
What's in ideploy.inc?

---

