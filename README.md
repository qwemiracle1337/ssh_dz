# case_1.  
Установка:
sudo apt install openssh-server -y
Проверка работы:
sudo systemctl status ssh
Result - running
# case_2.
1)Проверяю адрес ВМ командой в терминале:
ip a
2)Проверяю соединение
ping 192.168.56.2 в powershell
3)Подключился к ВМ через SSH командой:
& "C:\Windows\SysNative\OpenSSH\ssh.exe" mat@192.168.56.2
# case_3.
1)Создание файла прог_инженер.txt по пути C:\Users\radaev\ssh_dz\прог_инженер.txt
2)Копирую файл с хоста на ВМ командой:
& "C:\Windows\SysNative\OpenSSH\scp.exe" "C:\Users\radaev\Desktop\прог_инженер.txt" mat@192.168.56.2:~/ssh_dz/
3)Проверяю наличие файла командой:
ls ~/ssh_dz/
4)Копирую с хоста на ВМ командой:
& "C:\Windows\SysNative\OpenSSH\scp.exe" mat@192.168.56.2:~/ssh_dz/прог_инженер.txt "C:\Users\radaev\Desktop\from_vm_прог_инженер.txt"
# case_4.
1)Генерирую пару ключей командой 
& "C:\Windows\SysNative\OpenSSH\ssh-keygen.exe" -t ed25519 -C "mat@ssh_vm"
и дважды нажимаю enter для сохранения без пароля
Приватный ключ:C:\Users\radaev\.ssh\id_ed25519
Публичный ключ:C:\Users\radaev\.ssh\id_ed25519.pub
2)Копирую на Ubuntu в Virtual Box в свою домашнюю директорию
& "C:\Windows\SysNative\OpenSSH\scp.exe" "C:\Users\radaev\.ssh\id_ed25519.pub" mat@192.168.56.2:~/
3)Выполняю поиск файлов в вирутальной машине:
mat@mat-VirtualBox:~$ ls -l ~/.ssh/id_ed25519.pub
-rw-r--r-- 1 mat mat 92 Nov 13 05:16 /home/mat/.ssh/id_ed25519.pub
4)Осуществляется вход без пароля
ssh mat@192.168.56.2
