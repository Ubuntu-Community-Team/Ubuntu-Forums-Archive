---
title: "Java and Prolog"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by iso_9001 on 2010-03-11
hello everyone,

i have been struggling with a problem for a few days and even though i googled it and tried every possible solution, i could not manage to overcome what is bothering me. so i need your help.

i will try to explain my problem step by step in detail.

what i practically need is to connect java and prolog (eclipse and swi-prolog respectively) under ubuntu. i managed to do so under windows and i can run and compile my java code involving prolog code. what i did was to add an external jar (that is jpl.jar which creates a bidirectional bridge between java and prolog) to my project and add the jpl.dll directory to the environment variables (basically to my path). when i  run the code, it worked well and compiled and returned my query.

as the growing interest in open-source developments, i wanted to try the same thing under linux and chose ubuntu as my platform. however, i am having troubles and difficulties while trying to do the same thing here. the steps that i took are:

1. i downloaded eclipse (i can run a code and it gives me the output without anyproblem)
2. i downloaded swi-prolog and anlso jpl.jar
3. i created a project and added this jpl.jar to the project
4. i run the code and get the unsatisfiedLinkError which happened i believe due to the lack of dll file
5. the equivalent of this jpl.dll under ubuntu is libjpl.so
6. well the problem is this step.. no matter what i did or how hard i tried, i could not manage to add this path to the environment variables.

after searching the net a couple of days, i realized that there are some files including the strring "bash" and i followed many instructions. since, i had no luck and failed again.

some of the advices were to create a LD_LIBRARY_PATH for the directory that holds this libjpl.so and simply write it to these bash files (well i tried them one by one)..

here are the bash files i tried:

1. /etc/profile
2. ~/.bash_profile
3. ~/.profile
4. /etc/bash.bashrc
5. ~/.bashrc

some of these files gave the output of the command "echo $LD_LIBRARY_PATH" in the terminal and some of the did no even give the output. however, even though i can get the value of the env.var, i can get my code run. it still gives the error and claims that the jpl is missing. 

the directory where i hold my libjpl is: /usr/lib/swi-prolog/lib/i386
the line that i am writing to the bash file is: export LD_LIBRARY_PATH=/usr/lib/swi-prolog/lib/i386

i also tried to write these lines:
LD_LIBRARY_PATH=/usr/lib/swi-prolog/lib/i386
export LD_LIBRARY_PATH

PATH$:PATH: $LD_LIBRARY_PATH (there is no space between : and $ but left separated in order to avoid icons)
export PATH

but no luck! as i mentioned above, sometimes i could get the value in the terminal, however, when i start the eclipse, my project insists on not working. i even tried to run the code from terminal while i am getting the value of the env.var but still it did not work. i am confused and tired and wasted all the possible solutions i can find on the net. i also tried the /etc/environment file but no change at all..

so it would be really really helpful for me if any of you can direct me on:
1. on which file should i make the changes
2. what lines should i write?

i even wrote a simple code that outputs the java.library.path.. however, althoug i can get the value in the terminal, the output does not contain my libjpl.so path.. this also confuses me much.

if you require any further information, please do not hesitate to ask. if you want i can give the output of the command "echo $PATH" or "echo $LD_LIBRARY_PATH" or anything else..

thank you all in advance,

regards,

ismet

---

### Post by leinad177 on 2010-03-11
> **iso_9001 said:**
> 

PATH$:PATH: $LD_LIBRARY_PATH


lol! if you want to disable smileys just tick the box under the submit button

as for your current problem, im sorry to say that i have no idea

---

### Post by iso_9001 on 2010-03-11
well i did click the box for no icons but it did not seem to work somehow. anyway, thanks for the advice ;)

---

### Post by iso_9001 on 2010-03-11
has not anybody successfully defined the environment variables for jpl and connected eclipse with prolog yet?

even you know a little please help me as i really need the solutio.. 

thanks again

---

### Post by Mighty_Joe on 2010-03-11
> **iso_9001 said:**
> 
but no luck! as i mentioned above, sometimes i could get the value in the terminal, however, when i start the eclipse, my project insists on not working. 

I'm no Eclipse or Bash expert, but changing the environment in a terminal only changes it in that terminal (and, if exported, subshells). If you want to change the environment for Eclipse, you'll probably have to set your PATH and LD_LIBRARY_PATH in your .bashrc file.

---

### Post by iso_9001 on 2010-03-11
> **Mighty_Joe said:**
> I'm no Eclipse or Bash expert, but changing the environment in a terminal only changes it in that terminal (and, if exported, subshells). 

i did not define the variable in the terminal. i meant that after i defined the variable in one of these bash files, i checked the value through the terminal and i got the value back (well, if not for all, at least for some of them). however, when i tried it on eclipse i did not get the path with the libjpl.so path added. this might be because some other application or maybe a process is unsetting my variable.

> **Mighty_Joe said:**
>  If you want to change the environment for Eclipse, you'll probably have to set your PATH and LD_LIBRARY_PATH in your .bashrc file. 

that was one of the possible solutions that i tried. i opened the .bashrc file and added the line

export LD_LIBRARY_PATH=myPath

but did not work. 

the thing is, nobody is quite sure to change what file and what to write. i am confused that after i define the variable, i can get the value in the terminal but eclipse is unable to access to the path. since i am very new to linux family, i even dont know the differences of these bash files such as bash.bashrc and .bashrc or bash_profile and such. 

any further idea is greatly apprecaited. thanks

---

### Post by Mighty_Joe on 2010-03-11
> **iso_9001 said:**
> that was one of the possible solutions that i tried. i opened the .bashrc file and added the line
export LD_LIBRARY_PATH=myPath
but did not work. 


Did you log out and log back in?  .bashrc is run at login time.  Changing it will not change environment variables in the existing session.

> **iso_9001 said:**
> i even dont know the differences of these bash files such as bash.bashrc and .bashrc or bash_profile and such. 


[Bash Reference Manual: Startup Files]("http://www.gnu.org/software/bash/manual/bashref.html#Bash-Startup-Files").  
In Ubuntu, you'll want to put path variables in ~/.bashrc.

---

### Post by r-senior on 2010-03-11
You could try digging around in the menu to see what invokes Eclipse (I'm guessing a shell script), find where java is invoked to run Eclipse and pass the LD_LIBRARY_PATH using the -D option?

$ java -DLD_LIBRARY_PATH=xxx ...

If you are not already doing so, it might also be worth trying setting your Java environment to use Sun's JDK.

$  sudo update-java-alternatives -l

tells you what you are using.

$ sudo update-java-alternatives -s java-6-sun

would set the Sun JDK as the default, assuming it is installed.

$ sudo apt-get install sun-java6-jdk

would install it if it's not already installed, or use Synaptic.

---

### Post by iso_9001 on 2010-03-11
thank you both for the advices. 

i did log off and log in back but it did not do any good to me. some people argue that one should change the bash_profile instead of .bashrc, do you agree? what about bash.bashrc?

i also tried to run eclipse in the terminal. it did not work but i did not use the -D option. instead i tried to use the bash files and run the code in the terminal.

i am going to give a go to your suggestion and will report back in. 

thanks again

---

### Post by iso_9001 on 2010-03-11
hello everyone,

i tried your suggestions and could not get the code work. it still gives the same annoying error that is java.lang.unsatisfiedlinkerror: no jpl in java.library.path

i might as well be writing the path wrong. actually i am only writing the path of jpllib.so as the value of the LD_LIBRARY_PATH variable. this might be the reason. 

when i run the command echo $PATH in the terminal i get /usr/local/sbin:/usr/local/bin:/usr/bin:/sbin/:bin/:usr/games

when i run the command echo $LD_LIBRARU_PATH in the terminal i get /usr/lib/swi-prolog/lib/i386 (this is the directory where i keep libjpl.so file)

is there something wrong with this definition that i might give the value of the env. variable wrong? 

btw, i also tried to use the java method System.load("path") in order to include my libjpl.so in the java code but this also did not let my code run.. clearly i am missing something but what?

p.s.: the output of the java.library.path i get with a simple code is a little different from what i get from the echo $PATH in the terminal

output of code System.out.println(System.getProperty("java.library.path") is 

/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386:/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/xulrunner-1.9.1.3:/usr/lib/xulrunner-addons:/usr/lib/xulrunner-addons:/usr/java/packages/lib/i386:/usr/lib/jni:/lib:/usr/lib

and the output of the echo $PATH is

/usr/local/sbin:/usr/local/bin:/usr/bin:/sbin/:bin/:usr/games/usr/lib/swi-prolog/lib/i386

is it something related with this?

---

### Post by Mighty_Joe on 2010-03-11
> i might as well be writing the path wrong. actually i am only writing the path of jpllib.so as the value of the LD_LIBRARY_PATH variable. this might be the reason.

This is correct.  When you put a JAR in a CLASSPATH, you have to explicitly state the JAR file name. LD_LIBRARY_PATH works like PATH, where you specify directories, not the specific resources you're looking for.

SWI-Prolog has a [mailing list]("http://www.swi-prolog.org/Mailinglist.html").  It may be worthwhile to search and/or post to it. 

It sounds like you are running app from Eclipse.  You can set the environment in the project properties.  
Project->Properties->Run/Debug Settings->New (if necessary)->Environment

---

### Post by iso_9001 on 2010-03-11
well i also tried the environment tab in the eclipse run configuration screen but since i did not know what and how to define, i could not write the specifics correctly so it did not work. i could  not find any suggestion about it in the net and so i was stuck in that issue.

actually i would like to write you here what lines i add to the ~/.bashrc file:

LD_LIBRARY_PATH=/usr/lib/swi-prolog/bin/i386 (this path contains the libjpl.so file)
export LD_LIBRARY_PATH

i log-off and log back in. i open a terminal and write echo $LD_LIBRARY_PATH and it gives me the path as /usr/lib/swi-prolog/bin/i386
when i write echo $PATH it gives me the path.
java -version command also works and produces jdk 1.6.0.0 

but when i open eclipse and run the code as i do under windows, it gives the error. it keeps giving the error over and over. so what am i doing wrong? my head is going to explode soon :(

another possible solution that i tried is to manually add the library (i already added the libjpl.jar via build path-->add external jars option) to my project with the line:

System.load("/usr/lib/swi-prolog/bin/i386/libjpl.so"); 

although many people agreed that this line would successfully add the library to the project and will save the coder from defining the env. variables, the code still claims that there is no jpl in the java.library.path. 

i asked to some1 who managed to do what i am trying to do about this matter and he told me that he changed the .bash_profile file and added two lines i wrote above (LD_LIBRARY_PATH and exporting this path). as you would guess, that did not work, too..

i am running out of solutions :(

---

