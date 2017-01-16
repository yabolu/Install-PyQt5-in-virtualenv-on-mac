# Install-PyQt5-in-virtualenv-on-mac
step1: install Xcode
step2: 安装Qt5
step3: 获得你想要安装PyQt的python virtualenv, 我的是/Users/用户名/.virtualenvs/mytest/lib/python2.7/site-packages
step4: 安装sip
  tar zxvf sip包
  cd sip解压后的项目包
  python configure.py -d /Users/用户名/.virtualenvs/mytest/lib/python2.7/site-packages --arch x86_64
  make
  sudo make install
  我在这一步出现了错误: cp corporation denied 的错误
  解决方法: 重启电脑
           command + R 
           实用工具--> 终端: csrutil disable
           重启电脑
  sudo make clean
 
 step5: 安装PyQt5
    tar 解包
    cd 进入
    python configure.py --destdir /Users/用户名/.virtualenvs/mytest/lib/python2.7/site-packages --qmake /Applications/Qt5.5.0/5.5/clang_64/bin/qmake
    运行过程中出现了错误:Xcode not set up properly. You may need to confirm the license agreement by running /usr/bin/xcodebuild
    解决方法:
    打开文件: Qt_install_folder/5.7/clang_64/mkspecs/features/mac/default_pre.prf
    peplace isEmpty($$list($$system("/usr/bin/xcrun -find xcrun 2>/dev/null"))) with 
    isEmpty($$list($$system("/usr/bin/xcrun -find xcodebuild 2>/dev/null")))
    make 
    sudo make install 
    
           
