Dashboard de Análisis del Sector Turístico en Argentina (2023-2025)

Proyecto académico de análisis de datos. Es un dashboard interactivo en SAS Viya que permite monitorear los flujos de viajeros y la ocupación hotelera de cinco destinos argentinos, y proyectar la demanda del primer semestre de 2026.

Nota: este es un proyecto realizado en el marco de la carrera de Ciencias de Datos. El caso de negocio y el "cliente" son parte del ejercicio académico.

Objetivo

Automatizar la visualización y el análisis de los flujos de viajeros y de la ocupación hotelera. A diferencia de un reporte estático, el dashboard permite monitorear el rendimiento histórico de forma dinámica y estimar tendencias futuras, transformando datos complejos en información visual útil para la toma de decisiones.

Audiencia pensada: directivos de agencias de viajes y gerentes del sector hotelero. Por eso el diseño se apoya en indicadores clave (KPIs) y alertas rápidas por colores (semáforos), que permiten identificar oportunidades o riesgos de ocupación sin procesar las bases de datos a mano.

Problemática

El turismo en Argentina tiene una estacionalidad muy marcada, con picos en vacaciones y valles profundos en meses intermedios (por ejemplo, mayo). La dificultad central es prever ese comportamiento para ajustar la oferta de plazas. El dashboard integra una serie temporal de tres años (2023-2025) que permite:

Identificar qué destinos son más estables (como Buenos Aires o Mendoza).
Visualizar la dispersión de la demanda mediante gráficos de cajas.
Anticipar la carga del próximo semestre para planificar personal y promociones.
Funcionalidades
Filtros interactivos: botones de selección por año y controles deslizantes de fecha para aislar períodos específicos con un solo clic.
Gráficos dinámicos: mapa de burbujas animado y series temporales que reaccionan a los filtros.
Panel de KPIs: resumen ejecutivo con el total de viajeros (11 millones) y el porcentaje de ocupación real (68 %).
Tablas con reglas de visualización condicional (semáforos): permiten detectar rápidamente las plazas con bajo rendimiento de ocupación.
Proyección a futuro: estimación de viajeros para el primer semestre de 2026, con un horizonte de 6 meses y un intervalo de confianza del 95 %.
Drill-down: navegación desde la vista anual hasta el detalle mensual dentro de un mismo gráfico.
Datos

Fuente: dataset TURISMOARGENTO2023_2025, que consolida estadísticas de la Encuesta de Ocupación Hotelera (EOH) del INDEC y del Ministerio de Turismo.

Cobertura: datos mensuales de 5 ciudades (Salta, Bariloche, Córdoba, Mendoza y Buenos Aires) entre enero de 2023 y diciembre de 2025 (36 meses).

Variables principales:

Variable	Tipo	Descripción
ciudad	Categoría	Destino turístico. Dimensión principal para agrupar y filtrar
fecha	Fecha	Eje cronológico. Permite reconocer ciclos y aplicar la proyección
Total viajeros	Medida	Cantidad de personas que transitaron por el destino. Se agrega por suma para los KPIs
estadia_promedio_dias	Medida	Promedio de noches de permanencia de los turistas
ocupacion_pct	Medida	Porcentaje de la capacidad de camas utilizada. Activa las reglas de semáforo
Limpieza y transformación de datos
Estandarización temporal: se validó que el campo fecha fuera reconocido con formato cronológico y se eliminaron inconsistencias que pudieran romper la continuidad de la línea de tiempo. También fue necesario transformarlo en una secuencia continua para que el modelo de proyección reconociera la estacionalidad mensual sin errores.
Agregación de la medida principal: se configuró Total viajeros para que su agregación por defecto fuera la suma, y así obtener KPIs consolidados.
Jerarquías: se creó una jerarquía Ciudad → Año → Mes para habilitar el drill-down sin perder integridad de los datos.
Medidas calculadas: la métrica de ocupación real se usó como base de las reglas de semáforo (verde, amarillo y rojo según umbrales definidos para cada ciudad).
Filtros de fecha: se adaptó el rango temporal para que los controles deslizantes filtren los 36 meses de forma fluida.
Diseño visual
Visualización	Para qué se usó
KPIs y gráfico de cajas (box plot)	Mostrar el impacto total y la variabilidad de la demanda, e identificar las ciudades con comportamiento más errático
Mapa de burbujas animado	Geolocalizar el flujo turístico: el tamaño representa los viajeros y el color, el % de ocupación
Serie temporal con proyección	Identificar patrones estacionales y proyectar el primer semestre de 2026
Matriz de correlación	Validar la relación lineal (coeficiente 0,33) entre volumen de viajeros y eficiencia de ocupación

Criterio de color: escala de semáforo (verde para ocupación alta, amarillo para media, naranja/rojo para baja), con fondo limpio y líneas de cuadrícula sutiles para priorizar la lectura de picos y valores extremos.

Usabilidad: filtros de botones para años, deslizadores para meses, drill-down dentro de un mismo gráfico para evitar sobrecarga de información, y etiquetas del eje X rotadas 45° para mejorar la legibilidad.

Herramientas y habilidades aplicadas
SAS Viya (visualización y análisis)
Limpieza y preparación de datos
Series temporales y proyección con intervalo de confianza
Diseño de dashboards orientados a la toma de decisiones
Visualización de datos: KPIs, mapas, box plots y correlación

Autoría

Proyecto académico desarrollado por William Romero. Contacto: williamromero1548@gmail.com 
www.linkedin.com/in/williamromeroc
