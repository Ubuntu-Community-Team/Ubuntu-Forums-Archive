---
title: "Getting java to compile"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by ptpare on 2010-09-06
I am trying to learn the JAVA programming language but I am finding it very difficult to get past first base.
The problem seems to be with the CLASSPATH setting.
I am running Linux Ubuntu Hardy Heron and this is some of my terminal output.
I have eventually managed to compile SIUnits, List.java, Text.java, Graph.java and Display. java from Judith Bishop's book, Java Gently for Engineers and Scientists, but I can not get TrainTravel.java or any of the other programes in Chapter 2 of the book to compile.

I received the following output:
[PHP]bad class file: /home/phillip/java/javagently/Text.class
class file contains wrong class: javagently.Text
Please remove or make sure it appears in the correct subdirectory of the classpath.
           ("The journey covers " + Text.format(totalDistance,5,2) + " km");
                                    ^
1 error[/PHP]

Any help will be appreciated.
Thank you.
Regards

Phillip


The JDK version that I am using is as follows:

[PHP]phillip@voogdy-study:~/java/myprograms/ch2$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1~8.04.3)
OpenJDK Client VM (build 16.0-b13, mixed mode, sharing)
phillip@voogdy-study:~/java/myprograms/ch2$[/PHP]

My session history:

[PHP]phillip@voogdy-study:~$ echo $CLASSPATH

phillip@voogdy-study:~$ export CLASSPATH=~/java/:.
phillip@voogdy-study:~$ echo $CLASSPATH
/home/phillip/java/:.
phillip@voogdy-study:~$ javac Graph.java
javac: file not found: Graph.java
Usage: javac <options> <source files>
use -help for a list of possible options
phillip@voogdy-study:~$ cd java
phillip@voogdy-study:~/java$ cd javagently
phillip@voogdy-study:~/java/javagently$ ls
Display.java  List.class  List$Node.class  Text.java
Graph.java    List.java   Text.class
phillip@voogdy-study:~/java/javagently$ javac Graph.java
phillip@voogdy-study:~/java/javagently$ export CLASSPATH=$CLASSPATH:~/java/javagently/
phillip@voogdy-study:~/java/javagently$
phillip@voogdy-study:~/java/javagently$ echo $CLASSPATH
/home/phillip/java/:.:/home/phillip/java/javagently/
phillip@voogdy-study:~/java/javagently$ ls
Display.java   Graph$Dataset.class  List.class       Text.class
Graph$1.class  Graph.java           List.java        Text.java
Graph.class    Graph$Point.class    List$Node.class
phillip@voogdy-study:~/java/javagently$ rm *.class
phillip@voogdy-study:~/java/javagently$ ls
Display.java  Graph.java  List.java  Text.java
phillip@voogdy-study:~/java/javagently$ cd ..
phillip@voogdy-study:~/java$ cd ..
phillip@voogdy-study:~$ javac text.java
javac: file not found: text.java
Usage: javac <options> <source files>
use -help for a list of possible options
phillip@voogdy-study:~$ echo $CLASSPATH
/home/phillip/java/:.:/home/phillip/java/javagently/
phillip@voogdy-study:~$ cd java
phillip@voogdy-study:~/java$ cd javagently
phillip@voogdy-study:~/java/javagently$ ls
Display.java  Graph.java  List.java  Text.java
phillip@voogdy-study:~/java/javagently$ cd ..
phillip@voogdy-study:~/java$ cd ..
phillip@voogdy-study:~$ javac Text.java
javac: file not found: Text.java
Usage: javac <options> <source files>
use -help for a list of possible options
phillip@voogdy-study:~$ cd java
phillip@voogdy-study:~/java$ cd javagently
phillip@voogdy-study:~/java/javagently$ ls
Display.java  Graph.java  List.java  Text.java
phillip@voogdy-study:~/java/javagently$ javac Text.java
phillip@voogdy-study:~/java/javagently$ javac List.java
phillip@voogdy-study:~/java/javagently$ javac Graph.java
phillip@voogdy-study:~/java/javagently$ javac Display.java
Note: Display.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
phillip@voogdy-study:~/java/javagently$ ls
Display$1.class     Display$Watcher.class  Graph.java         List$Node.class
Display.class       Graph$1.class          Graph$Point.class  Text.class
Display$Data.class  Graph.class            List.class         Text.java
Display.java        Graph$Dataset.class    List.java
phillip@voogdy-study:~/java/javagently$ cd ..
phillip@voogdy-study:~/java$ cd myexamples
bash: cd: myexamples: No such file or directory
phillip@voogdy-study:~/java$ cd myprograms/
phillip@voogdy-study:~/java/myprograms$ ls
ch10  ch2  ch3  ch4  ch5  ch6  ch7  ch8  ch9
phillip@voogdy-study:~/java/myprograms$ cd ch2
phillip@voogdy-study:~/java/myprograms/ch2$ ls
DisplayWarning.java  NewFleet.java    SIUnits.class  TrainTravel.java
LiquidFlow.java      Resistance.java  SIUnits.java   TrigGraphs.java
phillip@voogdy-study:~/java/myprograms/ch2$ javac TrainTravel.java
TrainTravel.java:40: cannot access Text
bad class file: /home/phillip/java/javagently/Text.class
class file contains wrong class: javagently.Text
Please remove or make sure it appears in the correct subdirectory of the classpath.
           ("The journey covers " + Text.format(totalDistance,5,2) + " km");
                                    ^
1 error
phillip@voogdy-study:~/java/myprograms/ch2$ javac TrigGraphs.java
TrigGraphs.java:15: cannot access Graph
bad class file: /home/phillip/java/javagently/Graph.class
class file contains wrong class: javagently.Graph
Please remove or make sure it appears in the correct subdirectory of the classpath.
    Graph g = new Graph("Sine and Cosine","x","y");
    ^
1 error[/PHP]

---

### Post by yeats on 2010-09-06
You might get better help if you ask this question in the Development and Programming sub-forum, since programming issues like this are not really "Absolute Beginner" questions :-) : [http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

---

### Post by GregBrannon on 2010-09-06
Actually, these kind of questions belong in the "Programming Talk" forum.  Perhaps a mod will move it.

Since you've gotten the code in chapter 1 to compile and run, you're well past first base and have proven that you've gotten the JDK installed correctly and can accomplish the basic programming tasks from writing source code to running it.

So, I suspect there's something wrong with your code in the chapter 2 exercises or examples.  The error message is pointing to a problem with the Text.format() method or the Text class itself.

I don't think we'll be able to help you further without seeing some code.  Try to post code that focuses on the problem areas: the class containing the main() method and the Text class with its methods.  Hopefully, the chapter 2 code is fairly simple and short.

---

### Post by Ozymandias_117 on 2010-09-06
Might I suggest trying an IDE, such as Netbeans?

---

### Post by gauravj on 2010-09-07
I think the problem is with package hierarchy.
If you run from command line, you should be in bin directory
and the hierarchy shall be javagently/Text.class.
You fire *java javagently.Text* from bin directory.

---

### Post by ptpare on 2010-09-07
Thank you for all the responses. I have re-posted the question together with some of the java source code to [http://ubuntuforums.org/showthread.php?t=1569714](http://ubuntuforums.org/showthread.php?t=1569714) I intended to put it in "Programming Talk" but something went wrong and it landed up in a subforum - "Ubuntu Dev Link Forum". Perhaps a mod could move it for me. 
Please could I ask also for some help to find a tutorial on how to format posts to these forums in an appropriate way. For example, putting all code into boxes where appropriae.

Regards
Phillip

---

