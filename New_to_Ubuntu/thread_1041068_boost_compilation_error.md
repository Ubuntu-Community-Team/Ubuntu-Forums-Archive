---
title: "boost compilation error"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by bijay_panda on 2009-01-16
Hi,
I actually tried like bellow to compile a boost program and getting eror like.

bijay@cmp1:~/boost$ g++ -o second boostThread.cpp -L/user/lib/boost_filesystem-gcc42-1_34_1

/tmp/cceBBmFD.o: In function `main':
boostThread.cpp:(.text+0xeb): undefined reference to `boost::thread::thread(boost::function0<void, std::allocator<boost::function_base> > const&)'
boostThread.cpp:(.text+0x101): undefined reference to `boost::thread::join()'
boostThread.cpp:(.text+0x132): undefined reference to `boost::thread::~thread()'
boostThread.cpp:(.text+0x148): undefined reference to `boost::thread::~thread()'
collect2: ld returned 1 exit status

///////////////Here is my program//////////
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
///////////
installed path is like bellow

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

Please help me out.
Thanks in advance
Bijay Panda

---

