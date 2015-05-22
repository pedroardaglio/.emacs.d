;; AS CONFS ABAIXOS SÃO AS QUE JÁ VIERAM
(custom-set-variables
 ;; custom-set-variables was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(ansi-color-names-vector ["#2e3436" "#a40000" "#4e9a06" "#c4a000" "#204a87" "#5c3566" "#729fcf" "#eeeeec"])
 '(custom-enabled-themes (quote (manoj-dark)))
 '(ido-enable-flex-matching t))
(custom-set-faces
 ;; custom-set-faces was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(font-lock-function-name-face ((t (:foreground "deep sky blue" :weight light :height 1.0))))
 '(font-lock-keyword-face ((t (:foreground "red" :weight bold))))
 '(font-lock-variable-name-face ((t (:foreground "lime green")))))

;; Confs globais
(set-default-font "Monospace-10") ;; Fonte padrão
(setq electric-indent-mode -1) ;; Simplificando: Emacs é retardado e gosta de indentar do jeito dele
(setq-default indent-tabs-mode nil) ;; Sem tabs, apenas espaços
;;  q indent-line-function 'insert-tab) ;; Emacs retardado... novamente
(setq-default tab-width 4) ;; Indentação de 4 espaços
(setq-default indent-tabs-mode nil) ;; EMACS RETARDADO DA PORRA, EU QUERO DAR TAB QUANDO EU QUISER NESSA MERDA, FDP
(setq tab-stop-list (number-sequence 4 200 4))

;; Setando o ambiente para o python
(push "usr/bin" exec-path)
(setenv "PATH"
        (concat
         "/usr/bin" ":"
         (getenv "PATH")
         ))

;; Conf para o melpa
(require 'package)
(add-to-list 'package-archives
	     '("melpa" . "http://melpa.org/packages/") t)
;;(when (< emacs-major-version 24)
;;  (add-to-list 'package-archives '("gnu" . "http://elpa.gnu.org/packages/")))
(package-initialize)

;; Conf para meus packages instalados na mão
;; Tenho que adicionar cada diretório manualmente até eu descobrir como faz
;; isso dinamicamente D:
(add-to-list 'load-path "/home/pedro/.emacs.d/lisp_s")
(add-to-list 'load-path "/home/pedro/.emacs.d/lisp_m/neotree")
(add-to-list 'load-path "/home/pedro/.emacs.d/lisp_m/Pymacs")
;; To adicionando o caminho dos packages do melpa. Sei lá se tem que fazer isso
(add-to-list 'load-path "/home/pedro/.emacs.d/elpa")

;; melpa
(require 'simp)
(require 'fill-column-indicator)
(require 'flymake-python-pyflakes)
;; lisp_s
(require 'sr-speedbar)
;; lisp_m
(require 'neotree)
(require 'pymacs)
;; Outros que não sei daonde vieram. Devem existir junto com o Emacs
;; Retirei o 'ido abaixo, pois cansei dele e nao preciso desse require mais
;; (require 'ido)

;; Ruler para programacao - Nao uso mais, esta no python-mode-hook
;; (setq fci-rule-column 100)
;; (setq fci-rule-color "darkblue")
;; Desabilitar a toolbar
(tool-bar-mode -1)
;; Setar o encoding para iso-8859-1
(set-buffer-file-coding-system 'iso-8859-1)
;; Desabilitar o auto-save
(setq auto-save-default nil)
;; Exibir também a coluna do cursor
(column-number-mode)
;; Usando o ido.
;; (ido-mode t) ;; Cansei, é muito chato isso!

;; PYTHON FTW
;; (pymacs-load "ropemacs" "rope-")
;; (setq python-check-command "pyflakes")
;; (add-hook 'python-mode-hook 'flymake-python-pyflakes-load)
;; (setq flymake-python-pyflakes-executable "flake8")

;; meus atalhos :D
(global-set-key (kbd "s-<up>") 'windmove-up)
(global-set-key (kbd "s-<down>") 'windmove-down)
(global-set-key (kbd "s-<right>") 'windmove-right)
(global-set-key (kbd "s-<left>") 'windmove-left)
;; (add-hook 'text-mode-hook (global-set-key (kbd "<tab>") 'tab-to-tab-stop))
(global-set-key [f5] 'python-mode)
(global-set-key [f6] 'html-mode)
(global-set-key [f7] 'css-mode)
(global-set-key [f8] 'js-mode)
;; Falta colocar algo como 'sql-mode
(global-set-key [f9] 'neotree-toggle)

;; Adicionei globalmente o ruler
(define-globalized-minor-mode global-fci-mode fci-mode (lambda () (fci-mode 1)))
(global-fci-mode 1)

;; MEUS HOOKS
;; python-mode
(add-hook 'python-mode-hook
    (lambda () (setq fci-rule-column 80)
               (setq fci-rule-color "darkblue")
    )
)
;; Nao funfou. Quero algo que execute algo quando eu sair do python-mode
;; (add-hook 'python-mode-exit-hook
;;     (lambda () (setq fci-rule-column 30))
;; )
;; COISAS QUE FALTAM:
;; - Fazer as mudanças do Python somente quando eu for programar em python,
;;   não em todo o Emacs
