---
title: "Running Terminal commands - Error"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by flebber on 2010-11-22
I am having 2 small issues with running comandline apps for ruby. I am trying to install and run rvm and redcar.

I installed redcar with the sudo gem install redcar, That went fine.

I then installed redcar

```
sayth@sayth-homee:~$ /var/lib/gems/1.8/bin/redcar install
```
I then ran

and then tried to execute redcar.
```
Done! You're ready to run Redcar.
sayth@sayth-homee:~$ redcar
redcar: command not found
sayth@sayth-homee:~$ Redcar
Redcar: command not found

```

Similar issue with running the ruby manager rvm.

Install 
```
/var/lib/gems/1.8/bin/rvm-install
```
successful
```
Installation of RVM to /home/sayth/.rvm/ is complete.
```
try to use it
```
sayth@sayth-homee:~$ rvm use 1.9.2
No command 'rvm' found, but there are 20 similar ones
rvm: command not found

```

Any idea where I am going wrong?

---

### Post by cavh on 2010-11-22
You need to either:

1. CD into the directory holding the executable and issue the command from there; or
2. (better) update your PATH to include the folders where the executables are located.

You can do step 2 above by adding the following line to /home/your_user_name_here/.bashrc

```
export PATH = $PATH:/your/additional/paths/go/here
```

So, for example, if your redcar executable is in /opt/redcar/bin and the rvm executable is at /opt/ruby/bin, then the line will read as follows:

```
export PATH = $PATH:/opt/redcar/bin:/opt/ruby/bin
```

Once you have edited and saved the .bashrc file, close and reopen the terminal and try the commands you gave in your post (you can issue the commands from anywhere, you need not navigate to the location where the executables are).

---

### Post by flebber on 2010-11-24
So what's the best way to locate an executable, I can seem to locate the rvm executable.```
sayth@sayth-homee:~$ export PATH=$PATH:/opt/redcar/bin:/opt/ruby/bin
sayth@sayth-homee:~$ redcar
redcar: command not found
sayth@sayth-homee:~$ rvm
No command 'rvm' found, but there are 20 similar ones
rvm: command not found
sayth@sayth-homee:~$ rvm use 1.9.2
No command 'rvm' found, but there are 20 similar ones
rvm: command not found
sayth@sayth-homee:~$ 

```

edit

tried to grep binary but i haven got the command correct
```
sayth@sayth-homee:~$ grep --binary-files=TYPE redcar
grep: unknown binary-files type
sayth@sayth-homee:~$ grep --binary-files=redcar
grep: unknown binary-files type

```

---

### Post by flebber on 2010-11-24
No advice on how to find paths to update?

---

### Post by flebber on 2010-11-24
```
# paths
export PATH=$PATH:/var/lib/gems/1.8/bin:/home/sayth/.rvm/bin
```

---

