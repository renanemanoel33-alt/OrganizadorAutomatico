# Organizador
Meu Primeiro repertório de um organizador automático.
import os
from tkinter.filedialog import askdirectory
def organizar(organizador):
    pain=askdirectory(title='Selecione a pasta onde estão os arquivos')
    list=os.listdir(pain)
    local={
        'imagens':['.png','.jpg','.jpeg'],
        'documentos':['.pdf','.doc','.docx'],
        'musicas':['.mp3','.wav'],
        'videos':['.mp4','.avi'],
        'setup':['.exe','.msi'],
    }
    for arquivo in list:
        nome, extensao = os.path.splitext(f'{pain}/{arquivo}')
        for pasta in local:
            if extensao in local[pasta]:
                if not os.path.exists(f'{pain}/{pasta}'):
                    os.mkdir(f'{pain}/{pasta}')
            os.rename(f'{pain}/{arquivo}',f'{pain}/{pasta}/{arquivo}')
organizar('organizador')

