---
title: "boost compilation error,plz help"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by bijay_panda on 2009-01-16
Hi All,
I am new to boost.I already installed boost 1.34.1.
While compiling boost program like bellow

g++ -o second boostThread.cpp -lboost_filesystem

shows error like this 

/usr/bin/ld: cannot find -lboost_filesystem
collect2: ld returned 1 exit status

Can any one please help me to get rid of this.

Thanks in advance.
Bijay Panda.

---

### Post by baruch60610 on 2009-01-16
Hi, Bijay:

My guess would be that you are telling the compiler to use a library that doesn't exist.  You might want to double-check that there really is a boost_filesystem.

I don't know how to help you if it's really there.  You may need to give the actual path to this library (for example, if it's in /usr/lib, then maybe you need to put:

g++ -o second boostThread.cpp -l/usr/lib/boost_filesystem

Or whatever is the appropriate path to the library.  I hope this helps...

---

### Post by bijay_panda on 2009-01-16
Hi,
I got an error like bellow when i try with this path

bijay@cmp1:~/boost$ g++ -o second boostThread.cpp -L/user/lib/libboost_filesystem-gcc42-1_34_1

/tmp/cclxXala.o: In function `main':
boostThread.cpp:(.text+0xeb): undefined reference to `boost::thread::thread(boost::function0<void, std::allocator<boost::function_base> > const&)'
boostThread.cpp:(.text+0x101): undefined reference to `boost::thread::join()'
boostThread.cpp:(.text+0x132): undefined reference to `boost::thread::~thread()'
boostThread.cpp:(.text+0x148): undefined reference to `boost::thread::~thread()'
collect2: ld returned 1 exit status
bijay@cmp1:~/boost$ 
////Here is the installation path////
bijay@cmp1:~/boost$ locate libboost_filesystem
/usr/lib/libboost_filesystem-gcc41-mt-1_34_1.so.1.34.1
/usr/lib/libboost_filesystem-gcc42-1_34_1.so.1.34.1
/usr/lib/libboost_filesystem-gcc42-mt-1_34_1.so.1.34.1
/usr/lib/libboost_filesystem-gcc41-1_34_1.so.1.34.1
/var/cache/apt/archives/libboost_filesystem-gcc41-mt-1_34_1.so.1.34.1
/var/cache/apt/archives/libboost_filesystem-gcc42-1_34_1.so.1.34.1
/var/cache/apt/archives/libboost_filesystem-gcc42-mt-1_34_1.so.1.34.1
/var/cache/apt/archives/libboost_filesystem-gcc41-1_34_1.so.1.34.1
bijay@cmp1:~/boost$
////This is my program/////
#include <exception>
#include <boost/thread/thread.hpp>
#include <stdlib.h>
#include <iostream>
using namespace std;

class callable {
public:
    void run()
       {
         try 
	  {
             cout << "Throwing" <<std:: endl;
              throw string("error");
          } 
        catch(string &e) 
         {
           cout << "Error: " << e << endl;
         }
      }

    void operator()() {
        this->run();
    }
};

int main() {
    callable c;
    cout<<"inside main"<<endl;	
    boost::thread thd(boost::ref(c));
    thd.join();
    return 0;
} 

please please help me out to get rid of this.

---

