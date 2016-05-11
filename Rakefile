VERSION = '8u92'
URI_PATH = '8u92-b14'

task :clean do
  sh %{ rm -rf *.gz }
  sh %{ rm -rf jdk-* }
  sh %{ rm -rf ./pkg }
end

task :setup do
  sh %{ mkdir -p ./pkg }
end

task :download do
  sh %{ wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/#{URI_PATH}/jdk-#{VERSION}-linux-x64.tar.gz }
end

task :deb do
  # This is how we sidestep EULA
  sh %{ echo "y\n" | make-jpkg jdk-#{VERSION}-linux-x64.tar.gz }
  sh %{ mv *.deb ./pkg/ }
end

task :default => [ :clean, :setup, :download, :deb ]
