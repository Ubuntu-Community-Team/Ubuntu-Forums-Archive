---
title: "expecting &quot;)&quot;"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by quinche on 2009-05-22
I've been trying to run a code  and always get the same error "Syntax error: word unexpected (expecting ")")", can anyone tell me what can I do to solve this? Thanks

---

### Post by Mornedhel on 2009-05-22
You have a syntax error.

No one can tell you anything more unless you post the code (shell script ?) you are trying to execute.

---

### Post by Daveski on 2009-05-22
> **quinche said:**
> I've been trying to run a code  and always get the same error "Syntax error: word unexpected (expecting ")")", can anyone tell me what can I do to solve this? Thanks

Add a )
:D

---

### Post by ALIENDUDE5300 on 2009-05-22
Could you tell us what language the code is in, or at least open it in a text editor, and paste it here?

---

### Post by quinche on 2009-06-01
> **ALIENDUDE5300 said:**
> Could you tell us what language the code is in, or at least open it in a text editor, and paste it here?
This is the output that I've got:

~/Desktop/eig3.0/EIGENSTRAT$ ./example
bash: ./example: No such file or directory
linuxlab1234@ubuntu:~/Desktop/eig3.0/EIGENSTRAT$ ./example.perl
smartpca.perl -i example.geno  -a example.snp  -b example.ind  -k 2  -o example.pca  -p example.plot  -e example.eval  -l example.log  -m 5  -t 2  -s 6.0 
smartpca -p example.pca.par >example.log
../bin/smartpca: 1: Syntax error: word unexpected (expecting ")")
ploteig -i example.pca.evec -c 1:2  -p Case  -x  -y  -o example.plot.xtxt 
evec2pca.perl 2 example.pca.evec example.ind example.pca
smarteigenstrat.perl  -i example.geno  -a example.snp  -b example.ind  -p example.pca  -k 1  -o example.chisq  -l example.log 
smarteigenstrat -p example.chisq.par >example.log
../bin/smarteigenstrat: 1: Syntax error: word unexpected (expecting ")")
gc.perl example.chisq example.chisq.GC

and this is the code from the *.perl file:

#!/usr/bin/perl

$ENV{'PATH'} = "../bin:$ENV{'PATH'}"; 
# MUST put smartpca bin directory in path for smartpca.perl to work

$command = "smartpca.perl";
$command .= " -i example.geno ";
$command .= " -a example.snp ";
$command .= " -b example.ind " ;
$command .= " -k 2 ";
$command .= " -o example.pca ";
$command .= " -p example.plot ";
$command .= " -e example.eval ";
$command .= " -l example.log ";
$command .= " -m 5 ";
$command .= " -t 2 ";
$command .= " -s 6.0 ";
print("$command\n");
system("$command");

$command = "smarteigenstrat.perl "; 
$command .= " -i example.geno ";
$command .= " -a example.snp ";
$command .= " -b example.ind ";
$command .= " -p example.pca ";
$command .= " -k 1 ";
$command .= " -o example.chisq ";
$command .= " -l example.log ";
print("$command\n");
system("$command");

$command = "gc.perl example.chisq example.chisq.GC";
print("$command\n");
system("$command");

Thanks for the help,

---

### Post by Mornedhel on 2009-06-01
Your example.perl looks fine, aside from some bad coding form (no 'use strict' or warnings, and building a giant string to feed it to system()). By the way, the standard Perl extension is .pl, although that's only a convention and you can use anything.

According to :

> **quinche said:**
> ../bin/smartpca: 1: Syntax error: word unexpected (expecting ")")

and

> **quinche said:**
> ../bin/smarteigenstrat: 1: Syntax error: word unexpected (expecting ")")

The problem lies in the files smartpca and smarteigenstrat.

---

