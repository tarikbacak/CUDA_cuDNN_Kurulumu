# CUDA ve cuDNN'in Kurulması
Ubuntu 18.04 <br>
CUDA 11.5.2 <br>
cuDNN 8.3.2.44

## Sürücü
CUDA 11.5 için gerekli sürücü: >= 495.29.05

Sürücüyü kurabilmek için Ubuntu 18.04.5'i kurduktan sonra hiçbir güncelleme yapmadan direkt sürücüyü indiriyorum. Eğer güncelleme yaparsam sürücüyü kurduktan sonra yeniden başlatırken siyah ekranda takılı kalıyor.

## CUDA 11.5.2
[CUDA Dokümantasyon](https://developer.nvidia.com/cuda-11-5-2-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=18.04&target_type=deb_local
)<br>
[CUDA 11.5.2](https://developer.nvidia.com/cuda-11-5-2-download-archive?target_os=Linux)
aşağıdaki adımlar takip edilerek kurulur.<br>
1. `wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin`<br>
2. `sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600`<br>
3. `wget https://developer.download.nvidia.com/compute/cuda/11.5.2/local_installers/cuda-repo-ubuntu1804-11-5-local_11.5.2-495.29.05-1_amd64.deb`<br>
4. `sudo dpkg -i cuda-repo-ubuntu1804-11-5-local_11.5.2-495.29.05-1_amd64.deb`<br>
5. `sudo apt-key add /var/cuda-repo-ubuntu1804-11-5-local/7fa2af80.pub`<br>
6. `sudo apt-get update`<br>
7. `sudo apt-get -y install cuda`<br>

Kurulumu kontrol etmek için aşağıdaki kod çalıştırılır.<br>
 `md5sum cuda-repo-ubuntu1804-11-5-local_11.5.2-495.29.05-1_amd64.deb `<br>
[Bu link](https://developer.download.nvidia.com/compute/cuda/11.5.2/docs/sidebar/md5sum.txt
)ten çıkan 32 haneli şifre kontrol edilir.<br>
Bilgisayar yeniden başlatılır.
## cuDNN 8.3.2.44
[cuDNN Dokümantasyon](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html)<br>
cuDNN [bu link](https://developer.nvidia.com/rdp/cudnn-download)ten kayıt olunduktan sonra indirilir.<br>
cuDNN'in olduğu yerde terminal açılır ve aşağıdaki adımlar sırayla izlenir.<br>
1. `sudo dpkg -i cudnn-local-repo-ubuntu1804-8.3.2.44_1.0-1_amd64.deb`<br>
2. `sudo apt-key add /var/cudnn-local-repo-*/7fa2af80.pub`<br>
3. `sudo apt-get update` <br>
4. `sudo apt-get install libcudnn8=8.3.2.44-1+cuda11.5`<br>
5. `sudo apt-get install libcudnn8-dev=8.3.2.44-1+cuda11.5`<br>
6. `sudo apt-get install libcudnn8-samples=8.3.2.44-1+cuda11.5`<br><br>

cuDNN'in doğru kurulup kurulmadığı kontrol edilir.<br>
1. `cp -r /usr/src/cudnn_samples_v8/ $HOME`<br>
2. `cd  $HOME/cudnn_samples_v8/mnistCUDNN`<br>
3. `make clean && make`<br>
 Bu noktada eğer hata verirse şu kodu deneyebilirsiniz: <br>
 `sudo apt-get install libfreeimage3 libfreeimage-dev` <br>
4. `./mnistCUDNN`<br>
"Test passed!" çıktıysa cuDNN başarıyla kurulmuştur.<br>
Şimdi bilgisayarı yeniden başlatın.<br>
