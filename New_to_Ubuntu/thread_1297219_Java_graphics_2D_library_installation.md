---
title: "Java graphics 2D library installation"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by eman99 on 2009-10-21
Hi all,
    I need to run a .java file that includes some graph classes which need specific libraries that I don't think that I have on my machine. The reason that makes me suspect that is the error that I got when trying to compile this file, I got something like this:

x.java:3327: cannot find symbol
symbol  : class MyGraph
location: class x
double JRLSPC(MyGraph builder, int Conn[][] , double I[][], link L[], int nLinks, int flag_VL[], Path paths[], node ap[], flow_sol sol) throws IloException {

x.java:4854: cannot find symbol
symbol  : class AdjacencyMatrixGraph
location: class x
    AdjacencyMatrixGraph ng = new AdjacencyMatrixGraph(env.nnodes+1);
                                  ^
x.java:4855: cannot find symbol
symbol  : class PathFinder
location: class x
    PathFinder pf = new PathFinder(ng);
                        ^
Note: x.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
100 errors

Please help me download these missing libraries!

Thanks

---

### Post by Mighty_Joe on 2009-10-21
The Java package naming convention is to use one's TLD in reverse order. What is the fully qualified name of AdjacencyMatrixGraph or PathFinder?

---

### Post by eman99 on 2009-10-21
Thank you for your replay, but I am sorry I don't understand your question and how can I find this fully qualified name..?

---

### Post by Mighty_Joe on 2009-10-21
The fully qualified name of a class is the class name including the package.  For example, the fully qualified name of the String class is java.lang.String.  
When you write a Java class, you either have to specify the fully qualified name of a class every time you use it or specify an include statement that either has the fully qualified class or it's package.  Look for a block of "include" statements at the top of the class.

---

### Post by eman99 on 2009-10-21
Thanks, ok I think I got it, on the top I found the import list which I guess has what you asked for:

import ilog.concert.*; 
import ilog.cplex.*; 
import java.util.*;
import java.io.*;
//import javax.swing.*;
//import java.lang.reflect.Array;
import flanagan.plot.PlotGraph; 
import graphs.AdjacencyMatrixGraph;
//import graphs.bhandari_vertex; 
import graphs.Path;
import graphs.PathFinder;
import java.lang.reflect.Array;

This is from the file it self, please let me know if its not what you are asking for.

---

### Post by Mighty_Joe on 2009-10-21
That's what I was looking for, but it looks like someone repackaged the most likely classes.  If you do a [search]("http://www.google.com/search?q=AdjacencyMatrixGraph+PathFinder+Path") for the classes in question, you come up with a [likely source]("http://rollerjm.free.fr/pro/graphs.html"), but they use different package names.
Where did you get the source you are trying to compile?

---

### Post by eman99 on 2009-10-21
This file was created by a former college who give it to me and it is hard to contact him now. So what do you suggest to make this file running!

---

### Post by eman99 on 2009-10-21
Oh by the way I found the following class pathes are defined in his .bash file:

CLASSPATH=$CLASSPATH:/home/junit-4.3.1.jar
#CLASSPATH=$CLASSPATH:/home/java
CLASSPATH=$CLASSPATH:/home/flanagan.jar
CLASSPATH=$CLASSPATH:/home/code/mygraph
#CLASSPATH=$CLASSPATH:/home/code/rollerjm-graphs/src

#CLASSPATH=$CLASSPATH:/home/code/graphs
CLASSPATH=$CLASSPATH:/home/code

IT could give some clue!

---

### Post by Mighty_Joe on 2009-10-21
Do you have the source for the classes in question?  If so, you just need to include them in your classpath.  Have a look [here]("http://faq.javaranch.com/java/HowToSetTheClasspath") for how to fix that problem.
If you don't have the source, download it from the page I linked above.  You'll either need to change the import statements in your code or the packages on the downloaded code since they don't match.

---

### Post by eman99 on 2009-10-21
Ok so here is what happen:

I tried yesterday to download the adjacent matrix, pathfinder classes and I placed them in a folder then I added this path to my class path but it didn't work thats why I think I am missing some kind of library files which I have no idea where should I place it!


Note: when I search for j2sdk folder in my system I get no result!

---

### Post by Mighty_Joe on 2009-10-22
I don't know how I missed your post at 04:46 PM yesterday.  Do you have flanagan.jar?  The classes may be in there.  If you have it, run jar -tf flanagan.jar and post the output.
If you don't have it, I'll tell you how to correct your classpath problem.

---

### Post by eman99 on 2009-10-22
It is ok, thank you for your help.

I downloaded the flanagan.jar 2 days ago and I placed it under my home directory/code folder.
so when I run the command this is the output:

eman@eman-laptop:~$ cd code
eman@eman-laptop:~/code$ run jar -tf flanagan.jar
bash: run: command not found
eman@eman-laptop:~/code$ jar -tf flanagan.jar
META-INF/
META-INF/MANIFEST.MF
flanagan/
flanagan/analysis/
flanagan/analysis/BetaFunct.class
flanagan/analysis/BetaFunction.class
flanagan/analysis/BoxCox.class
flanagan/analysis/BoxCox.java
flanagan/analysis/BoxCoxFunction.class
flanagan/analysis/ChiSquareFunct.class
flanagan/analysis/CorrCoeff.class
flanagan/analysis/Cronbach.class
flanagan/analysis/Cronbach.java
flanagan/analysis/EC50Function.class
flanagan/analysis/EngsetLoad.class
flanagan/analysis/EngsetProb.class
flanagan/analysis/ErlangBfunct.class
flanagan/analysis/ErlangCfunct.class
flanagan/analysis/ErlangFunction.class
flanagan/analysis/ErrorProp.class
flanagan/analysis/ErrorProp.java
flanagan/analysis/ExponentialFunction.class
flanagan/analysis/ExponentialMultipleFunction.class
flanagan/analysis/ExponentialProbPlotFunc.class
flanagan/analysis/ExponentialSimpleFunction.class
flanagan/analysis/FdistribtionFunct.class
flanagan/analysis/FFfunct.class
flanagan/analysis/fFunct.class
flanagan/analysis/FrechetFunctionOne.class
flanagan/analysis/FrechetFunctionTwo.class
flanagan/analysis/FrechetProbPlotFunc.class
flanagan/analysis/GammaFunct.class
flanagan/analysis/GammaFunction.class
flanagan/analysis/GaussianFunct.class
flanagan/analysis/GaussianFunction.class
flanagan/analysis/GaussianFunctionFixed.class
flanagan/analysis/GaussProbPlotFunc.class
flanagan/analysis/GumbelFunction.class
flanagan/analysis/GumbelMaxProbPlotFunc.class
flanagan/analysis/GumbelMinProbPlotFunc.class
flanagan/analysis/LogEC50Function.class
flanagan/analysis/LogisticFunction.class
flanagan/analysis/LogisticProbPlotFunc.class
flanagan/analysis/LogNormalThreeParFunct.class
flanagan/analysis/LogNormalThreeParFunction.class
flanagan/analysis/LogNormalThreeParProbPlotFunc.class
flanagan/analysis/LogNormalTwoParFunct.class
flanagan/analysis/LogNormalTwoParFunction.class
flanagan/analysis/LogNormalTwoParProbPlotFunc.class
flanagan/analysis/LorentzianFunction.class
flanagan/analysis/LorentzianProbPlotFunc.class
flanagan/analysis/ParetoFunctionOne.class
flanagan/analysis/ParetoFunctionTwo.class
flanagan/analysis/ParetoProbPlotFunc.class
flanagan/analysis/PCA.class
flanagan/analysis/PCA.java
flanagan/analysis/PoissonFunction.class
flanagan/analysis/ProbabilityPlot.class
flanagan/analysis/ProbabilityPlot.java
flanagan/analysis/RankAnalysis.class
flanagan/analysis/RankAnalysis.java
flanagan/analysis/RayleighFunctionOne.class
flanagan/analysis/RayleighFunctionTwo.class
flanagan/analysis/RayleighProbPlotFunc.class
flanagan/analysis/RectangularHyperbolaFunction.class
flanagan/analysis/Regression.class
flanagan/analysis/Regression.java
flanagan/analysis/RegressionDerivativeFunction.class
flanagan/analysis/RegressionDerivativeFunction.java
flanagan/analysis/RegressionDerivativeFunction2.class
flanagan/analysis/RegressionDerivativeFunction2.java
flanagan/analysis/RegressionFunction.class
flanagan/analysis/RegressionFunction.java
flanagan/analysis/RegressionFunction2.class
flanagan/analysis/RegressionFunction2.java
flanagan/analysis/Scores.class
flanagan/analysis/Scores.java
flanagan/analysis/SigmoidHillSipsFunction.class
flanagan/analysis/SigmoidThresholdFunction.class
flanagan/analysis/Stat.class
flanagan/analysis/Stat.java
flanagan/analysis/StepFunctionFunction.class
flanagan/analysis/StudentTfunct.class
flanagan/analysis/WeibullFunct.class
flanagan/analysis/WeibullFunctionOne.class
flanagan/analysis/WeibullFunctionTwo.class
flanagan/analysis/WeibullProbPlotFunc.class
flanagan/circuits/
flanagan/circuits/CoaxialLine.class
flanagan/circuits/CoaxialLine.java
flanagan/circuits/Impedance.class
flanagan/circuits/Impedance.java
flanagan/circuits/ImpedSpecModel.class
flanagan/circuits/ImpedSpecModel.java
flanagan/circuits/ImpedSpecRegression.class
flanagan/circuits/ImpedSpecRegression.java
flanagan/circuits/ImpedSpecRegressionFunction1.class
flanagan/circuits/ImpedSpecRegressionFunction1.java
flanagan/circuits/ImpedSpecRegressionFunction2.class
flanagan/circuits/ImpedSpecRegressionFunction2.java
flanagan/circuits/ImpedSpecSimulation.class
flanagan/circuits/ImpedSpecSimulation.java
flanagan/circuits/ParallelPlateLine.class
flanagan/circuits/ParallelPlateLine.java
flanagan/circuits/Phasor.class
flanagan/circuits/Phasor.java
flanagan/circuits/PhasorMatrix.class
flanagan/circuits/PhasorMatrix.java
flanagan/circuits/TransmissionLine.class
flanagan/circuits/TransmissionLine.java
flanagan/circuits/TwoWireLine.class
flanagan/circuits/TwoWireLine.java
flanagan/complex/
flanagan/complex/Complex.class
flanagan/complex/Complex.java
flanagan/complex/ComplexErrorProp.class
flanagan/complex/ComplexErrorProp.java
flanagan/complex/ComplexMatrix.class
flanagan/complex/ComplexMatrix.java
flanagan/complex/ComplexPoly.class
flanagan/complex/ComplexPoly.java
flanagan/control/
flanagan/control/AtoD.class
flanagan/control/AtoD.java
flanagan/control/BlackBox.class
flanagan/control/BlackBox.java
flanagan/control/ClosedLoop.class
flanagan/control/ClosedLoop.java
flanagan/control/Compensator.class
flanagan/control/Compensator.java
flanagan/control/DelayLine.class
flanagan/control/DelayLine.java
flanagan/control/DtoA.class
flanagan/control/DtoA.java
flanagan/control/FirstOrder.class
flanagan/control/FirstOrder.java
flanagan/control/HighPassPassive.class
flanagan/control/HighPassPassive.java
flanagan/control/LowPassPassive.class
flanagan/control/LowPassPassive.java
flanagan/control/OpenLoop.class
flanagan/control/OpenLoop.java
flanagan/control/Prop.class
flanagan/control/Prop.java
flanagan/control/PropDeriv.class
flanagan/control/PropDeriv.java
flanagan/control/PropInt.class
flanagan/control/PropInt.java
flanagan/control/PropIntDeriv.class
flanagan/control/PropIntDeriv.java
flanagan/control/SecondOrder.class
flanagan/control/SecondOrder.java
flanagan/control/ZeroOrderHold.class
flanagan/control/ZeroOrderHold.java
flanagan/integration/
flanagan/integration/DerivFunction.class
flanagan/integration/DerivFunction.java
flanagan/integration/DerivnFunction.class
flanagan/integration/DerivnFunction.java
flanagan/integration/IntegralFunction.class
flanagan/integration/IntegralFunction.java
flanagan/integration/Integration.class
flanagan/integration/Integration.java
flanagan/integration/RungeKutta.class
flanagan/integration/RungeKutta.java
flanagan/interpolation/
flanagan/interpolation/BiCubicSpline.class
flanagan/interpolation/BiCubicSpline.java
flanagan/interpolation/CubicSpline.class
flanagan/interpolation/CubicSpline.java
flanagan/interpolation/PolyCubicSpline.class
flanagan/interpolation/PolyCubicSpline.java
flanagan/interpolation/QuadriCubicSpline.class
flanagan/interpolation/QuadriCubicSpline.java
flanagan/interpolation/TriCubicSpline.class
flanagan/interpolation/TriCubicSpline.java
flanagan/io/
flanagan/io/Db.class
flanagan/io/Db.java
flanagan/io/DigiGraph.class
flanagan/io/DigiGraph.java
flanagan/io/FileChooser.class
flanagan/io/FileChooser.java
flanagan/io/FileInput.class
flanagan/io/FileInput.java
flanagan/io/FileInputAsChar.class
flanagan/io/FileInputAsChar.java
flanagan/io/FileNameSelector.class
flanagan/io/FileNameSelector.java
flanagan/io/FileOutput.class
flanagan/io/FileOutput.java
flanagan/io/FileTypeFilter.class
flanagan/io/FileTypeFilter.java
flanagan/io/KeyboardInput.class
flanagan/io/KeyboardInput.java
flanagan/io/MultipleFilesChooser.class
flanagan/io/MultipleFilesChooser.java
flanagan/io/PrintToScreen.class
flanagan/io/PrintToScreen.java
flanagan/math/
flanagan/math/ArrayMaths.class
flanagan/math/ArrayMaths.java
flanagan/math/BetaFunct.class
flanagan/math/ChiSquareFunct.class
flanagan/math/Conv.class
flanagan/math/Conv.java
flanagan/math/Copy of TimeAndDate.java
flanagan/math/Ffunct.class
flanagan/math/Fmath.class
flanagan/math/Fmath.java
flanagan/math/FourierTransform.class
flanagan/math/FourierTransform.java
flanagan/math/GammaFunct.class
flanagan/math/GaussFunct.class
flanagan/math/LogNormalThreeParFunct.class
flanagan/math/LogNormalTwoParFunct.class
flanagan/math/Matrix.class
flanagan/math/Matrix.java
flanagan/math/Maximisation.class
flanagan/math/Maximisation.java
flanagan/math/MaximisationFunction.class
flanagan/math/MaximisationFunction.java
flanagan/math/Maximization.class
flanagan/math/Maximization.java
flanagan/math/MaximizationFunction.class
flanagan/math/MaximizationFunction.java
flanagan/math/Minimisation.class
flanagan/math/Minimisation.java
flanagan/math/MinimisationFunction.class
flanagan/math/MinimisationFunction.java
flanagan/math/Minimization.class
flanagan/math/Minimization.java
flanagan/math/MinimizationFunction.class
flanagan/math/MinimizationFunction.java
flanagan/math/OverDetermined.class
flanagan/math/PsRandom.class
flanagan/math/PsRandom.java
flanagan/math/StudentTfunct.class
flanagan/math/TimeAndDate.class
flanagan/math/TimeAndDate.java
flanagan/optics/
flanagan/optics/FunctTE.class
flanagan/optics/FunctTEplot.class
flanagan/optics/FunctTEsuper.class
flanagan/optics/FunctTM.class
flanagan/optics/FunctTMplot.class
flanagan/optics/FunctTMsuper.class
flanagan/optics/GratingCoupler.class
flanagan/optics/GratingCoupler.java
flanagan/optics/PlanarWaveguide.class
flanagan/optics/PlanarWaveguide.java
flanagan/optics/PrismCoupler.class
flanagan/optics/PrismCoupler.java
flanagan/optics/Reflectivity.class
flanagan/optics/Reflectivity.java
flanagan/optics/RefractiveIndex.class
flanagan/optics/RefractiveIndex.java
flanagan/optics/RegressFunct.class
flanagan/physchem/
flanagan/physchem/Donnan.class
flanagan/physchem/Donnan.java
flanagan/physchem/DonnanConcn.class
flanagan/physchem/DonnanConcn.java
flanagan/physchem/DonnanMinim.class
flanagan/physchem/DonnanMinim.java
flanagan/physchem/FunctionPatX.class
flanagan/physchem/GCSminim.class
flanagan/physchem/GCSminim.java
flanagan/physchem/GouyChapmanStern.class
flanagan/physchem/GouyChapmanStern.java
flanagan/physprop/
flanagan/physprop/IonicRadii.class
flanagan/physprop/IonicRadii.java
flanagan/physprop/Pva.class
flanagan/physprop/Pva.java
flanagan/physprop/RefrIndex.class
flanagan/physprop/RefrIndex.java
flanagan/physprop/Saline.class
flanagan/physprop/Saline.java
flanagan/physprop/Sucrose.class
flanagan/physprop/Sucrose.java
flanagan/physprop/Water.class
flanagan/physprop/Water.java
flanagan/plot/
flanagan/plot/Plot.class
flanagan/plot/Plot.java
flanagan/plot/PlotGraph.class
flanagan/plot/PlotGraph.java
flanagan/plot/PlotPoleZero.class
flanagan/plot/PlotPoleZero.java
flanagan/roots/
flanagan/roots/RealRoot.class
flanagan/roots/RealRoot.java
flanagan/roots/RealRootDerivFunction.class
flanagan/roots/RealRootDerivFunction.java
flanagan/roots/RealRootFunction.class
flanagan/roots/RealRootFunction.java
eman@eman-laptop:~/code$ 

so now what?

---

### Post by Mighty_Joe on 2009-10-22
That was just a shot in the dark.  What you need to understand is [how Java finds classes]("http://java.sun.com/javase/6/docs/technotes/tools/findingclasses.html") (scroll down to "How the Java Launcher Finds User Classes").  Note the following:
> A class file has a subpath name that reflects the class's fully-qualified name.
If you download the source file for org.rollerjm.graph.PathFinder, you need to create a series of nested directories named org/rollerjm/graph and put the PathFinder file in the "graph" directory.  If you created those nested directories in a directory named "code", you would add "code" to the classpath.  
When the JVM needs to load a class, it is going to look through the classpath for the root package name (in our example, "org"). Finding a likely candidate, it will traverse down that directory to find the class file.

---

### Post by eman99 on 2009-10-22
I have tried that, this is the classpaths that I defined in my .profile and .bashrc:

 
CLASSPATH=/usr/local/ilog/cplex90/lib/cplex.jar
CLASSPATH=/home/eman/junit-4.3.1.jar
CLASSPATH=/home/eman/junit-4.3.1-src.jar
CLASSPATH=/home/eman/code/flanagan.jar
CLASSPATH=/home/eman/code/graph
CLASSPATH=/home/eman/code
export CLASSPATH

the pathes are exactly where I placed the .jar files and the pathfinder, adjacencymatrix .java files.
but it is still not working. by the way for th definition of the classpath I also tried to write them as follow:

 
CLASSPATH=$CLASSPATH:/usr/local/ilog/cplex90/lib/cplex.jar
CLASSPATH=$CLASSPATH:/home/eman/junit-4.3.1.jar
CLASSPATH=$CLASSPATH:/home/eman/junit-4.3.1-src.jar
CLASSPATH=$CLASSPATH:/home/eman/code/flanagan.jar
CLASSPATH=$CLASSPATH:/home/eman/code/graph
CLASSPATH=$CLASSPATH:/home/eman/code
export CLASSPATH

and also this way:
CLASSPATH=.:/usr/local/ilog/cplex90/lib/cplex.jar
CLASSPATH=.:/home/eman/junit-4.3.1.jar
CLASSPATH=.:/home/eman/junit-4.3.1-src.jar
CLASSPATH=.:/home/eman/code/flanagan.jar
CLASSPATH=.:/home/eman/code/graph
CLASSPATH=.:/home/eman/code
export CLASSPATH

non of them work!

---

### Post by Mighty_Joe on 2009-10-22
You are leaving out some critical information. What package is PathFinder in?  Where did you put it in the filesystem? How do you import it into your source?  
Note that, according to the "How the Java Launcher Finds User Classes" link, you aren't supposed to point CLASSPATH to the directory PathFinder is in, but the root of a path that corresponds to the class' package name.

---

### Post by eman99 on 2009-10-22
Now this is the problem I guess, I just download this rollerjm-graphs package because I thought it will have the necessary libraries to run the unknown classes that the compiler can't see when try to run the source file. And this is why I am asking for help! if you can advise me what to download and where to place them to make this file run..! please note that I am not very profissional in dealing with linux system so I would appreciate if you can make it easy to understand and follow..!

best regards

---

### Post by Mighty_Joe on 2009-10-22
I'm trying to help, but you have to do your homework.  I can't see what is on your computer. You keep leaving out vital information, as I said in my last post. 
You say you downloaded "this rollerjm-graphs package".  What file name did you download?  I didn't see this file in the classpath settings you posted at 02:58 PM.

---

### Post by eman99 on 2009-10-22
ok, sorry about the lack of information that I am providing..
I downloaded file called 20040307-1815-rollerjm-graphs.zip then I extracted its content which is a folder name rollerjm-graphs I placed it on the following path (I might be wrong by selecting this path but this is what I have done) /home/code/rollerjm-graphs
in this subfolder there are the following folders:
build
doc
lib
src
test
rollerjm-graphs.jar

now the adjacencyMatrixGraph.java, Dijkstra.java, IGraph.java, Path.java, and PathFinder.java files are located on the following path:
/home/code/rollerjm-graphs/src/org/rollerjm/graph

another .jar file called junit.jar is located on the path: /home/code/rollerjm-graphs/lib

all these files are exist after I extracted the .zip file that I mintioned on the beginning

please let me know if you need further detailes!

---

### Post by Mighty_Joe on 2009-10-23
If you look at the contents of rollerjm-graphs.jar (jar -tf), you'll see that it contains the class files that you require.  Add it to your class path and it should resolve the dependencies you are looking for.

---

### Post by eman99 on 2009-10-24
This is what I got when I run the rollerjm-graphs.jar

eman@eman-laptop:~/code$ cd rollerjm-graphs/
eman@eman-laptop:~/code/rollerjm-graphs$ jar -tf rollerjm-graphs.jarMETA-INF/
META-INF/MANIFEST.MF
org/
org/rollerjm/
org/rollerjm/example/
org/rollerjm/graph/
org/rollerjm/example/LetterGraph.class
org/rollerjm/example/LetterGraphBuilder.class
org/rollerjm/example/LetterGraphFinder.class
org/rollerjm/graph/AdjacencyMatrixGraph.class
org/rollerjm/graph/Dijkstra$PriorityQueue$QueueElement.class
org/rollerjm/graph/Dijkstra$PriorityQueue.class
org/rollerjm/graph/Dijkstra.class
org/rollerjm/graph/IGraph.class
org/rollerjm/graph/Path.class
org/rollerjm/graph/PathFinder.class
eman@eman-laptop:~/code/rollerjm-graphs$ 


so now what should I add to my classpath? 
could you please give me the correct way (I mean the command) to write the class path and where like in my .profile or .bashrc or both?

---

### Post by Mighty_Joe on 2009-10-26
> **eman99 said:**
> 
could you please give me the correct way (I mean the command) to write the class path and where like in my .profile or .bashrc or both?

It looks like the JAR file contains the classes you need, correct?
I gave you a link to how to set the classpath [four days ago]("http://ubuntuforums.org/showpost.php?p=8141834&postcount=9").

---

### Post by eman99 on 2009-10-26
correct but when I tried this, I mean after adding the classpaths I still have the same compilation errors!

---

### Post by Mighty_Joe on 2009-10-27
We've covered a lot of ground and we need to regroup.
What is your classpath (i.e. "echo $CLASSPATH")?
Do all the JAR files in the CLASSPATH exist? If you have directories in the CLASSPATH, what is in those directories?
What is the output from javac?

---

### Post by eman99 on 2009-10-27
All .jar files appears when I run the echo $CLASSPATH:

eman@eman-laptop:~$ echo $CLASSPATH
/usr/local/ilog/cplex90/lib/cplex.jar:/home/eman/junit-4.3.1.jar:/home/eman/junit-4.3.1-src.jar:/home/eman/code/flanagan.jar:/home/eman/code/graph:/home/eman/code/mygraph:/home/eman/code:/home/eman/code/rollerjm-graphs/org/rollerjm/graph
eman@eman-laptop:~$ 

but I still have the problem when compile my file, here is part of  what I got:


eman@eman-laptop:~$ javac -classpath /usr/local/ilog/cplex90/lib/cplex.jar x.java 
                                           
x.java:2737: incompatible types
found   : <nulltype>
required: int
            int length = paths[k].getLength() + 1;
                                              ^
x.java:3146: operator + cannot be applied to Path.getLength,int
            int length = paths[k].getLength() + 1;
                                           ^
x.java:3146: incompatible types
found   : <nulltype>
required: int
            int length = paths[k].getLength() + 1;
                                              ^
x.java:4854: cannot find symbol
symbol  : class AdjacencyMatrixGraph
location: class x
    AdjacencyMatrixGraph ng = new AdjacencyMatrixGraph(env.nnodes+1);
    ^
x.java:4854: cannot find symbol
symbol  : class AdjacencyMatrixGraph
location: class x
    AdjacencyMatrixGraph ng = new AdjacencyMatrixGraph(env.nnodes+1);
                                  ^
x.java:4855: cannot find symbol
symbol  : class PathFinder
location: class x
    PathFinder pf = new PathFinder(ng);
    ^

x.java:4855: cannot find symbol
symbol  : class PathFinder
location: class x
    PathFinder pf = new PathFinder(ng);
                        ^
Note: x.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
100 errors

---

### Post by Mighty_Joe on 2009-10-28
Two things:
I don't see rollerjm-graphs.jar in the CLASSPATH.  That's where AdjacencyMatrixGraph and related files are.
If you specify a -classpath argument to javac, it will ignore the CLASSPATH environment variable.

---

### Post by eman99 on 2009-10-28
Ok so I tried to add the rollerjm-graphs.jar to the classpath ==> nothing changed,

then I deleted the classpath from the javac command line (javac x.java) 
==> nothing changed


then I added the classpaths to all .jar files to the command line 
(eman@eman-laptop:~$ javac -classpath /usr/local/ilog/cplex90/lib/cplex.jar:/home/eman/code/rollerjm-graphs/rollerjm-graphs.jar x.java )
==> again no changes..!!!!

any thoughts?

---

### Post by Mighty_Joe on 2009-10-28
I notice in [this post]("http://ubuntuforums.org/showpost.php?p=8141598&postcount=5") you said you had "import graphs.AdjacencyMatrixGraph" in your source.  
Note that that same class in the JAR file from rollerjm.free.fr uses a different package: org.rollerjm.graph.AdjacencyMatrixGraph.

---

