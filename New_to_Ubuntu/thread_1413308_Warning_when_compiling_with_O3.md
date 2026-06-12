---
title: "Warning when compiling with O3"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by newport_j on 2010-02-22
When I complied my code using option O3 instead of O0, I got the error:

InitializeScenarioData.c: In function ‘InitializeScenarioData’:
InitializeScenarioData.c:41: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result


I am not sure what the complier is talking about. It seems to not mind this when I compile with option O0, but minds very much (or warns very much) when compiling with option O3, which then gives me this error. This is not the only line were that error occurs. I am just showing one occurrence for simplicity.

Any help appreciataed.

Newport_j

---

### Post by avidday on 2010-02-22
There is a difference between an error and a warning. What the compiler is reporting is a warning, which is an informational message telling the compiler thinks there might be something wrong with your code, even though it is syntactically correct enough to be compiled.

In this case, the plain English meaning is exactly what the compiler warning text says. The fscanf function returns a value (and that value has important meaning if you are using the function correctly), but your code is ignoring it.

---

### Post by newport_j on 2010-02-24
That seems correct. The question is why did the compiler complain (show a warning statement) when I compiled with the gcc compiler flag -O3 and not when I complied with the gcc compiler flag -O0? I do not know what the other flags would produce (-O1 and -O2).

Newport_j

---

### Post by avidday on 2010-02-26
The answer (20 seconds work with Google, you might want to try it some time), can be found here [https://wiki.ubuntu.com/CompilerFlags](https://wiki.ubuntu.com/CompilerFlags).

Ubuntu have instrumented libc and added a default compile option, active only for "release" setting (-O2 or higher), which warns on unsafe use of certain libc functions. fscanf is one such function.

---

